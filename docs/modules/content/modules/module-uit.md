# Uitdatabank

Met deze module kunnen redacteurs activiteiten synchroniseren naar de Uit in Vlaanderen databank.

De synchronisatie naar UiT gebeurt op basis van records in elastic. De synchronisatie kan asynchroon en kan, omwille van performantie redenen, op worker pods gedaan worden


## Elastic configuratie

Vermits de naamgeving van de content types per site kan verschillen hebben we een extra ‘Uit type’ veld voorzien dat standaard op event (activiteit) en place (locatie) is gezet. Hierdoor kunnen verschillende sites op eenvoudige wijze hun content types mappen naar de standaard Elastic configuratie die nodig is om de sync succesvol te laten verlopen. 


**Aandachtspunten bij de configuratie :**

* Component type, Mapper en Schema veldnaam liggen vast
* Uit type value ligt vast : event voor activiteit en place voor locatie
* Elastic configuratie kan per site geactiveerd worden 


### Content type Locatie (place)

Aandachtspunt : Een aantal velden zijn niet verplicht in de redactie maar wel verplicht voor de synchronisatie

| Verplicht  | component type | component naam | Mapper       |Schema veldnaam in Elastic |
|------------|----------------|----------------|--------------|---------------------------|
| X          |Naam locatie.   |Standaard titel |Titel Mapper  |title                      |
| X          |Adres           |Adres           |Value Mapper  |adress                     |
|x|Info|Tekstvak met opmaak|Value mapper|description location|
|x|Uit in vlaanderen taxonomie|Uit in vlaanderen taxonomie|Uit taxonomy|naamgeving is automatisch|
|x|Uit Type|Tekstlijn|Tekst Mapper|uit_type (value : place)|

### Content type Activiteit (Event)

Aandachtspunt : Een aantal velden zijn niet verplicht in de redactie maar wel verplicht voor de synchronisatie

| Verplicht  | component type | component naam | Mapper       |Schema veldnaam in Elastic |
|------------|----------------|----------------|--------------|---------------------------|
|x|Titel|Standaard titel / Tekstlijn|Titel Mapper / Tekst Mapper|title|
|x|Teaser|(standaard) Tekstvak met opmaak|Teaser mapper / Tekstmapper|summary|
|x|Hoofdafbeelding|Afbeelding|Value mapper|image|
|x|Locatie|Content referentie|Content Ref Link Mapper|location_ref|
||Prijzen|CCC : Prijs|Value mapper|price|
|x|Tijdstippen of periode|Paragraaf Tijdstip Vaste periode|Value mapper|time_periods|
|x|Uit synchronisatie|Keuzevak|Tekst Mapper|uit_sync (value : sync-to-uit)|
||Minimum leeftijd|Nummer|Tekst Mapper|min_age|
||Maximum leeftijd|Nummer|Tekst Mapper|max_age|
|x|Basistarief|Keuzelijst|Tekst Mapper|base_price|
|x|Uit in vlaanderen taxonomie|Uit in vlaanderen taxonomie|Uit taxonomy|naamgeving is automatisch|
|x|Uit Type|Tekstlijn|Tekst Mapper|uit_type (value : event)|

## WCM admin

Toegang is enkel beschikbaar voor beheerders

* ACC : https://wcm-admin-a.antwerpen.be/home
* PROD : https://wcm-admin.antwerpen.be/home

**Werkwijze**
Per tenant (websites in de interface) kan de Uitdatabank module geactiveerd worden.

In de configuratie van de Uitdatabank BSL kan er configuratie per site toegevoegd worden:

```json
"moduleConfig": {
    "sites": [
      {
        "uuid": "[site-uuid]",
        "indexName": "[elastic engine naam zonder de language suffix]",
        "contributors": [
          "email@domain.be",
          "email2@domain.be",
          /* lijst van gebruikers die toegang moeten hebben tot de events in de uitdatabank interface */
        ],
        "languages": [
          "[taal-suffix-1]",
          "[taal-suffix-2]"
          /* lijst van talen die gebruikt worden in de site */
        ]
      },
      {
        "uuid": "[site-uuid]",
        "indexName": "[elastic engine naam zonder de language suffix]",
        "contributors": [
          "email@domain.be",
          "email2@domain.be",
          /* lijst van gebruikers die toegang moeten hebben tot de events in de uitdatabank interface */
        ],
        "languages": [
          "[taal-suffix-1]",
          "[taal-suffix-2]"
          /* lijst van talen die gebruikt worden in de site */
        ]
      }
    ]
}

```

## UiT Synchronisatie

### Redactioneel

* de redacteur maakt de activiteit aan , publiceert deze en zet de Uit integratie aan
* we kunnen nog niet conditioneel indexeren dus alle activiteiten worden naar elastic gesynced
* de ‘Sync naar UiT’ flag bepaalt of de activiteit effectief naar UiT wordt gestuurd (value  : 0 of 1)
* **Opgelet :**  een aantal velden zijn optioneel in de redactie maar verplicht voor de synchronisatie !


### Synchronisatie flow

* Via een cron (frequentie te bepalen) worden de activiteiten opgehaald uit Elastic (op basis van Last indexed & sync Flag)

* Per activiteit wordt via een call naar tussentabel gecheckt of het om een update of een insert gaat (delete wordt niet ondersteund)

* Indien de activiteit nog niet gesynced werd naar UiT  wordt een check gedaan of alle velden die nodig zijn voor de synchronisatie naar UiT ingevuld zijn.

* Indien **niet** alle verplichte velden heeft
  - wordt de sync onderbroken
  - wordt de fout gelogd in het logboek
  - wordt een entry aangemaakt in de tussentabel (met Statuscode 1)


* Indien de activiteit alle verplichte velden heeft  : 

*************** SYNC LOCATIE ********************
   
* wordt de locatie opgehaald uit Elastic (op basis van location_ref)


* wordt een call gedaan naar de tussentabel om te checken of deze reeds gesynced is naar UiT 
  - Indien aanwezig in tussentabel wordt via de last modified bepaald of een update naar UiT nodig is 
    * Indien update nodig wordt er gesynced naar UiT :
      - bij succesvolle sync naar UiT : update tussentabel
      - bij fout bij sync : 
        - wordt de fout gelogd in het logboek
        - gebeurt er geen update in tussentabel
        - wordt de sync NIET onderbroken (er is immers een Locatie ID)

  - Indien de locatie niet in de tussentabel zit wordt deze aangemaakt in UiT (Place model)
    - bij succesvole synchronisatie naar UiT :  :
      - wordt gelogd in het logboek 
      - wordt een entry aangemaakt in de tussentabel  (met Statuscode 0)
    - indien de synchronisatie fout loopt :  
      - wordt de fout gelogd in het logboek 
      - wordt de synchronisatie stop gezet
      - worden er twee entries aangemaakt in de tussentabel
        - entry voor de locatie (met Statuscode 3)
        - entry voor de activiteit (met Statuscode 4)

Enkel indien de locatie succesvol werd gesynced naar UiT wordt de Activiteit gesynced

*************** SYNC ACTIVITEIT ********************

**Indien het om een insert gaat :**

* bij succesvole synchronisatie naar UiT :
  * wordt gelogd in het logboek 
  * wordt een item weggeschreven naar de tussentabel  (met Statuscode 0)

* indien de synchronisatie fout loopt :  
  * wordt de fout gelogd in het logboek 
  * wordt een entry aangemaakt in de tussentabel  (met Statuscode 4)


**Indien het om een update gaat :**

* bij succesvolle synchronisatie naar UiT :
  * wordt gelogd in het logboek
  * wordt de tussentabel geüpdate
* indien de synchronisatie fout loopt :  
  * wordt gelogd in het logboek 
  * update tussentabel (Statuscode 4, syncDate wordt niet aangepast)


**Aandachtspunt :**

in het geval dat een andere locatie is geselecteerd in een bestaande activiteit en de synchronisatie van deze locatie loopt fout dan blijft de oude locatie van kracht in UiT.


## Cron / retry logica

### Settings

**ACCeptatie**

* [CRON_FREQ]       : Elke minuut
* [Terug in TIJD]   : 5 minuten 
* [Clean up]        : Elke minuut
* [Elke nacht]      : Elke minuut

**PRODuctie**

* [CRON_FREQ]       : Elke 10 minuten op het uur (14u00 / 14u10 / 14u20 / ….)
* [Terug in TIJD]   : 2 uur 
* [Clean up]        : Elke 10 minuten (14u05 / 14u15 / 14u25 / ….)
* [Elke nacht]      : Taxonomy update

### Retry/Sync logica : 

Haal alle activiteiten op uit elastic waar last_indexed >  [Current_time] - [Terug in TIJD]

Check per activiteit of er een item in de tussentabel zit 

* Als het item in de tussentabel zit

  * Als het Item reeds succesvol gesynced is : 
    * check of syncDate tussentabel < last_indexed
      * true  : doe sync naar UiT (update)
      * false : doe niets  : er is geen update in elastic sinds de laatste sync

  * Als het item in de tussentabel zit en niet succesvol gesynced is :
    * check of syncDate tussentabel > [Current_time] - [Terug in TIJD]
      * True : doe sync (INSERT) naar UiT
      * False : doe niets, het aantal retries is overschreden (in het voorbeeld wordt 12 keer geprobeerd)


**Als het Item niet in tussentabel zit**

* doe sync naar UiT (insert)
* insert record in tussentabel (zowel bij  success als fail)

### (Mongo) Tussentabel


| Schema  | Type |Value |
|------------|----------------|---------------------------|
|ContentId|String|id van het content item|
|ContentType|String|activiteit / Locatie|
|syncDate|Date|datum waarop de sync werd gedaan|
|lockTime|Date||
|Error|Number| SUCCESS = 0, EVENT_MISSING_REQUIRED_FIELDS = 1,PLACE_MISSING_REQUIRED_FIELDS = 2, ERROR_UIT_SYNC_LOCATION = 3, ERROR_UIT_SYNC_EVENT = 4, ERROR_UIT_SYNC_IMAGE = 5|
|info|String||
|uitId|String|id van het evenement in de UiT databank,  0 indien de sync fout is gegaan|
|uitUrl|String|url van het evenement in de UiT databank,  0 indien de sync fout is gegaan 
|owner|Boolean||
|siteId|String|site waarvoor de synchronisatie gedaan werd, wordt in wcm-admin geconfigureerd|
|tenantId|String|tenant waartoe de site behoort|
|indexName|String|engine die gebruikt wordt voor de synchronisatie, wordt in wcm-admin geconfigureerd|
