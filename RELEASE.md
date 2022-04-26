# Release Notes GPubP - Content beheer 

Hier vind je de release notes van **GPubP - Content beheer** (aka **De Redactie**, aka **WCMv4**), één van de onderdelen van het [Generiek Publicatie Platform](https://acpaas.digipolis.be/nl/product/generiek-publicatie-platform). 

*Lees [hier meer](#legende) over het formaat en de structuur van deze release notes.*

## Index
| Release 	| Datum 	| Inhoud 	| Status 	|
|---	|---	|---	|---	|
| [4.4.1](#441-2022) 	| 2022 	| Bynder Beeldenbank en Chat ondersteuning | [![Generic badge](https://img.shields.io/badge/Contrib-TODO-teal.svg)]() 	|
| [4.4.0](#440-2022-05-30) 	| 30 mei 2022 	| Meertaligheid 	| [![Generic badge](https://img.shields.io/badge/Core-ACC-blue.svg)]() 	|
| [4.3.0](#430-2022-05-30) 	| 30 mei 2022 	| Werken met Navigatie Menu's, URL patronen en sitestructuren 	| [![Generic badge](https://img.shields.io/badge/Core-ACC-blue.svg)]() 	|
| [1.0.0](#100-2022-04) 	| april 2022 	| Logboek module 	| [![Generic badge](https://img.shields.io/badge/Contrib-DEV-yellow.svg)]() 	|
| [1.0.0](#100-2022-04) 	| april 2022 	| Verzendmodule voor (o.a.) nieuwsbrieven 	| [![Generic badge](https://img.shields.io/badge/Contrib-DEV-yellow.svg)]() 	|
| [4.2.1.hotfix-6](#421hotfix-6-2022-04-14) 	| 14 april 2022 	| Noodzakelijke fixes op productie 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.2.1.hotfix-5](#421hotfix-5-2022-03-24) 	| 24 maart 2022 	| Noodzakelijke fixes op productie 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.2.1.hotfix-4](#421hotfix-4-2022-03-10) 	| 10 maart 2022 	| Noodzakelijke fixes op productie 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.2.1.hotfix-3](#421hotfix-3-2022-03-03) 	| 03 maart 2022 	| Noodzakelijke fixes op productie 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.2.1.hotfix-2](#421hotfix-2-2022-02-24) 	| 24 feb 2022 	| Enkele fixes rond uitgifte tijdstip (PZA) | [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.2.1.hotfix-1](#421hotfix-1-2022-02-17) 	| 17 feb 2022 	| Fix voor werken met 10+ navigatiebomen 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.2.1](#421-2022-02-14) 	| 14 feb 2022 	| Uitbreidingen voor PZA 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [4.1.5](#415-2022-01-10) 	| 10 jan 2022 	| Rubens release voor A-Stad 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|
| [1.0.0](#100-2021-12-23) 	| 23 jan 2022 	| Tabel content component 	| [![Generic badge](https://img.shields.io/badge/Contrib-PROD-Green.svg)]() 	|
| [4.1.2](#412-2021-12-14) 	| 14 dec 2021 	| MVP Release 	| [![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]() 	|

---

## [4.4.1]: 2022
[![Generic badge](https://img.shields.io/badge/Contrib-TODO-teal.svg)]()
- Beelden in [Bynder](https://www.bynder.com/) kunnen gekozen worden door de redacteur rechtstreeks uit de Redactie.
- [Teleportel](https://www.teleportel.com/) ondersteuning

## [4.4.0]: 2022-05-30
[![Generic badge](https://img.shields.io/badge/Core-ACC-blue.svg)]()

> **MTA**
> 
> gepland op: 6/4, 15/4, 29/4 en 13/5

- Per site configureer je de talen
- Allerlei instellingen zoals de site url, preview url gaan taalgevoelig worden
- Content beheerders bepalen welke content componenten van een content type vertaalbaar zijn en welke niet.
- Redacteurs werken aan content voor een specifieke taal. 
- Een content item wordt gemaakt in een bepaalde taal. Heb je 4 vertalingen, dan zijn dit 4 content items
- Er komt een taalaaduiding in het content overzicht
- Bij het maken van een nieuw content item moet eerst nog een taalkeuze gemaakt worden.
- Per content item kan je eenvoudig zien in welke talen dit reeds vertaald is.

## [4.3.0]: 2022-05-30
[![Generic badge](https://img.shields.io/badge/Core-ACC-blue.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15728).

> **MTA**
> 
> gepland op: 6/4, 15/4, 29/4 en 13/5

### Added
- **Navigatie:** 
  - Site beheerders kunnen het `URL patroon` van een content type `instellen op site niveau`, zo kan dit anders ingericht worden per site. 
	> **Nota voor afnemers!** 
	>
	> *We nemen standaard het URL patroon over van wat er ingesteld is op tenant niveau van elk content type*.
  - Er kan gewerkt worden met `URL patroon variabele` voor de opbouw van een URL
  - Ontwikkelaars zullen nooit meer URL's moeten samenstellen in code. De URL's zijn onderdeel van elk content item.
  	> **Nota voor afnemers!** 
  	>
  	> *Je kan nu URL patronen veel dynamischer instellen. Kijk de code na en verwijder alle hardcoded regels rond het opbouwen/samenstellen van een URL in de frontend code*.
  - Bij het wijzgingen van een URL patroon, kan je `in bulk` alle content items `bijwerken naar dit nieuw URL patroon`.
  - Als Redacteur kan je het pad (gedeelte voor de slug) aanpassen als je hiervoor rechten hebt. Zo kan je `afwijken van het vooropgestelde URL Patroon` voor je content item.
  - Via een Feature toggle kan je de `Menu feature de/activeren` voor je site
  - Via de API kan ik `alle informatie van een menu opvragen` voor een site
	> **Nota voor afnemers!** 
	>
	> *Menu's werden hiervoor beheerd in de Navigation UI. Op aanvraag kunnen we je bestaande menu's migreren zodat ze vanaf nu vanuit de redactie kunnen beheerd worden.*
	> *Voor frontend developers is het belangrijkste dat er **geen** navigatie data meer zal bestaan op content items*.
	> ```javascript
	> // Het volgende stuk verdwijnt van de payload bij het ophalen van een content item:
	> ...
	> "modulesData": {
    >   "navigation": {
    >      "navigationTree": "1608",
    >      "id": 140219
    >   }
	> }
	> ...
	>```
  - Er kunnen zoveel menu's als gewenst gemaakt worden
  - Per menu registratie kunnen extra attributen geregistreerd worden (bv een icon code)
  - Als redacteur kan je met menu's werken vanuit één content item of vanuit het `volledig menu overzicht`
  - Menu items kunnen `gesorteerd` worden
  - Menu items kunnen op andere plekken worden gezet, inclusief alle onderliggende kinderen
  - Een menu item kan een registratie van en content item zijn, een externe url of een tussentitel
  - Een content item kan één of meerdere keren voorkomen in éénzelfde of een ander menu.
  - Content items in een menu houden rekening met de publicatiestatus, maw het menu item is enkel actief als het content item zelf gepubliceerd is. Je kan aangeven dat het menu item automatisch mee geactiveerd wordt wanneer het content item gepubliceerd wordt.
  - Er kan per content type aangegeven worden welke menu's door de redacteurs gebruikt mogen worden.
- **Content** 
  - Er is een nieuw content item info-kaartje dat de essentie van het content item weergeeft in een kaartje. 
  - Als Content Beheerder kan ik een formulier referentie verplicht of optioneel maken
  - Als Content Beheerder kan ik de label instellingen voor een formulier referentie inrichten
- **Search** 
  - Er is een basis versie waarmee content van een site geïndexeerd wordt in Elastic App Search
  - Per content type kan aangegeven worden of het geïndexeerd moet worden of niet en welke afbeelding mee in de elastic index moet geregistreerd worden
  - Een volledige her-indexatie kan gestart worden vanuit de Redactie. 
  - Afbeelding worden in elastic opgenomen via publiek bereikbare URL's. Deze root hiervan kan in de Redactie ingesteld worden.
  

### Changed
- **Navigatie:** 
  - Via een Feature toggle kan je de `Sitestructuur feature de/activeren` voor je site
  	> **Nota voor afnemers!** 
	>
	> *Redacteurs konden content items in de navigatiestructuur plaatsen voordien. Dit is nu vervangen door uitgebreidere sitestructuur features*
  - Via de API kan ik `alle informatie van een sitestructuur opvragen` voor een site. Hier kan je alle onderliggende items in een structuur opvragen dat dikwijls gebruikt wordt bij overzichtspagina's voor het tonen van de 'child' pagina's. Anderzijds kan je ook alle bovenliggende elementen in de sitestrucuur opvragen voor bijvoorbeeld het opbouwen van een broodkruimel.
	> **Nota voor afnemers!** 
	>
	> *Navigatie werdt hiervoor beheerd deels in de redactie, deels in de Navigation UI. Op aanvraag kunnen we je bestaande navigatie migreren naar de nieuwe sitestructuur zodat ze volwaardig via de redactie kunnen beheerd worden.*
	> *Voor frontend developers is het belangrijkste dat er **geen** navigatie data meer zal bestaan op content items*.
	> ```javascript
	> // Het volgende stuk verdwijnt van de payload bij het ophalen van een content item:
	> ...
	> "modulesData": {
    >   "navigation": {
    >      "navigationTree": "1608",
    >      "id": 140219
    >   }
	> }
	> ...
	>```
  - Er is slechts één sitestructuur (per taal) per site, zo vormt dit de fysieke samenhang tussen content items
  - Een content item heeft één primaire/hoofd plaats in de sitestructuur. Daarnaast kan dat zelfde content item extra secundaire voorkomens hebben in de sitestructuur. Deze laatste zijn als het ware virtuele entries
  - Een sitestructuur item kan een registratie van en content item zijn, een externe url of een tussentitel
  - Sitesitructuur items kunnen `gesorteerd` worden
  - Content items in de sitestructuur houden rekening met de publicatiestatus, maw het item in de structuur is enkel actief als het content item zelf gepubliceerd is. Je kan aangeven dat het item in de sitestructuur automatisch mee geactiveerd wordt wanneer het content item gepubliceerd wordt.
  - Als content beheerder kan ik per content type bepalen hoe redacteurs content in de site structuur kunnen plaatsen. Ofwel niet, ofwel met beperkingen ofwel een kunnen ze een vrije plaats in de structuur kiezen voor het content item.
  - Indien het content item enkel een vaste plaats heeft in de sitestructuur dan gaan we het niet fysiek registreren. Zo voorkomen we dat duizende nieuws berichten bijvoorbeeld in de sitestructuur geplaatst worden. Het systeem weet wel waar precies waar deze content zou staan. 
- **Tabel**
  - Label van de actieknop aangepast bij het toevoegen van cell info
  - Je kan nu een cell eenvoudiger leegmaken.  
  
### Fixed
Een 50-tal bug fixes waarvan de belangrijkste:
- **Content** 
  - Linken naar afbeeldingen in een tekstvak met opmaak zijn gefixed
  - Cross site content referentie werkt nu terug wanneer je het content item bewerkt
  - Adres content component verliest de gekozen waarde niet meer
  - Zoeken naar content kan nu ook obv de slug
  - De GIS referentie gaf een verkeerde waarde terug bij de recyclageparken laag
  - Filter op status 'gearchiveerd' werkt zoals het hoort
  - Soms kon je een tabel niet bewerken omdat het ergen achter verscheen.
- **API** 
  - de $exist operator voor filteren in views werkt nu wel zoals verwacht


## [1.0.0]: 2022-03
[![Generic badge](https://img.shields.io/badge/Core-DEV-yellow.svg)]()
- **Verzendmodule** 
  - De verzendmodule is gemaakt voor PZA om zo automatisch mogelijk nieuwsbrieven naar de pers te sturen. 
  - Er kunnen verschillende verzendkanalen worden opgezet.
  - Per kanaal wordt de content bepaalt en waar het naar verzonden moet worden.
  - SendGrid (e-mail campagne systeem) is de eerste verzendmethode. het systeem voorziet dat andere verzendmethodes ingeplugd kunnen worden.
  - Er kan ad hoc, één per één en in bulk verstuurd worden al dan niet time based.
- **Logboek**
  - Er is een logboek dat de verzendgebeurtenissen weergeeft. 
  - Het logboek kan ook door andere modules gebruikt worden in het systeem om zo een goe beeld te krijgen wat en wanneer er allemaal gebeurt. 
  - Het logboek kan een handig hulpmiddel zijn voor troubleshooting. 

## [4.2.1.hotfix-6]: 2022-04-14
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()

### Fixed
- het verwijderen van een navigatie item volgt de nieuwe werkwijze van de recent aangepast navigatie engine ([zie Digipolis nieuws](https://nieuws.digipolis.be/project/46359))

## [4.2.1.hotfix-5]: 2022-03-14
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15801).
### Fixed
- **Content:** De cache zal sneller worden opgebouwd waardoor er minder 'oeps, pagina niet gevonden' zal voorkomen
- **Navigatie:** enkele kleinere fixes rond het gebruik van de navigatie engine

## [4.2.1.hotfix-4]: 2022-03-10
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15793).
### Added
- **Navigatie:** Aanpassing waarbij we eenvoudig (tijdelijk) de navigatiestructuur voor A-Stad van Acc naar Prd kunnen overzetten

### Fixed
- **Content**
  - Automatisch starten bij video component is gefixed
  - Pagina's kunnen opnieuw worden aangemaakt in de redactie
  - Transities worden nu ook geladen voor gebruiker die enkel workflow read-rechten hebben


## [4.2.1.hotfix-3]: 2022-03-03
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15792).
### Added

### Fixed
- **Content** 
  - Views kunnen nu correct gefiltered worden obv taxonomie term(en)
  - Het gekozen adres (via de location picker) wordt nu correct bewaard in de redactie
  - Instellingen van de voorvertoning module worden nu correct bewaard

## [4.2.1.hotfix-2]: 2022-02-24
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15788).
### Fixed
- **API:** Fix die het duidelijker maakt wanneer een content item gelocked is door een redacteur in de Redactie
- **Content** 
  - De uitgifte datum van een content item kan ondanks het veld readonly is, toch leeggemaakt worden. 
  - De uitgifte datum wordt niet aangepast aan de laatste publicatiedatum, ook al is dit zo geconfigureerd
- **Preview:** Fix waarbij de preview instelling op site niveau niet correct bewaard werd

---

## [4.2.1.hotfix-1]: 2022-02-17
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()


-  **Navigatie:** Er is een issue ontdekt waarbij redacteurs hun navigatieboom niet meer kunnen kiezen in de keuzelijst. De dropdown toont enkel de eerste 10 entries. We gaan hier in de hotfix zorgen dat er 20 items opgehaald worden, een betere oplossing staat op de backlog weliswaar. Hiermee kunnen de afnemers vandaag meteen verder.  


## [4.2.1]: 2022-02-14
[![Generic badge](https://img.shields.io/badge/Core-PROD-Green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15727).
### Added
-  **API** 
   -  Content schrijven kan via de WCM Content Manager API op [deze manier](https://docs.google.com/document/d/1cMGpDkgqBnVhzlr7nr00YK8xciIESvIX1YmffqT6VzE/edit#heading=h.xhcpij33fl32).
   -  Bij gebruik van een paragraaf zal er in de payload (meta) van een Content Item een `componentType` en `componentName` uitkomen die respectievelijk het type en de systeemnaam van dat Content Component in de paragraaf bevat.
-  **Content** 
	- Extra configuratie opties voor een `Tekstvak met Opmaak`. Je kan nu bepalen of er met afbeeldingen of interne linken gewerkt mag worden. ([Meer info](https://docs.google.com/document/d/19RHSpMWIhUoD4ST7d4fvd1Z-mqxb14shNrsly_mDGs4/edit#heading=h.i6gktat17chj))
		> **Nota voor afnemers!** 
		>
		> *Content Beheerders gaan alle Tekstvak met Opmaak content componenten moeten herconfigureren en een keuze maken van deze nieuwe opties. De content zelf moet niet gemigreerd worden*.
	- Een nieuw `Formulier Referentie` content component waarmee je een formulier kan kiezen dat gemaakt is via de Form Composer. ([Meer info](https://docs.google.com/document/d/19RHSpMWIhUoD4ST7d4fvd1Z-mqxb14shNrsly_mDGs4/edit#heading=h.imvkzfzdczxy))
    - Audio component met ondersteuning voor SoundCloud. ([Meer info](https://docs.google.com/document/d/19RHSpMWIhUoD4ST7d4fvd1Z-mqxb14shNrsly_mDGs4/edit#heading=h.awwnu5ldhyxd))
	- Voor componenten die bestaan uit `waardelijsten` (key/value) zoals keuzerondjes, keuzelijsten, etc, kan je de data ervan eenvoudig `importeren` in de Redactie.
	- Een extra configuratie optie voor `adres/locatie` component waar je nu het zoekbereik kan instellen zoals zoeken in adres, straatnamen, districten, pleinen, ... ([Meer info](https://docs.google.com/document/d/19RHSpMWIhUoD4ST7d4fvd1Z-mqxb14shNrsly_mDGs4/edit#heading=h.xsig90b1a2in))
	- `Tekstlijn` component krijgt extra configuratie opties waarmee je een `masker` kan invoeren. Handig voor o.a bankrekening nummers, rijksregister nummers, personeel codes, etc.
	- Alle autocomplete velden zullen een 'clear' (x) optie krijgen zodat je een nieuwe zoek kan lanceren in de lijst
	- Content kan nu met een `uitgifte datum` gepubliceerd worden. Deze is verschillend van de publicatiedatum. De eerste kan in het verleden gezet worden om zo historische content te kunnen overzetten in de Redactie. De laatste is altijd de effectieve systeemdatum wanneer iets gepubliceerd wordt. 
-  **Rollen & Rechten:** Vaak zijn er externe toepassingen die content willen toevoegen of aanpassen via de API. Hiervoor is er een nieuw type gebruiker `acpaasConsumerApplications` in de Redactie. Gebruikers van dit type zijn geen individueen of personen maar stellen eerder een toepassing voor. Zo kunnen we met het rollen en rechten systeem ook fijnmazig bepalen wat welke toepassing mag doen. 

### Changed
-  **Content** 
   -  We hebben het navigeren met de browser back knop verbeterd. Wanneer je een filter hanteert op het content overzicht, zal deze onthouden worden wanneer je hier naar terugkeert. 
    - Als redacteur kan je de keuze die je maakte in een keuzelijst eenvoudig 'clearen'.

### Fixed
-  **API:** Content item dat niet gevonden werd resulteerd nu in een HTTP 404 in plaats van een HTTP 400.
-  **Content** 
   -  Wanneer je een compartiment maakte met de naam 'status' gaf dit een fout.
   -  Wijzigingen aan een Custom Content Component worden nu correct weerspiegeld in Content Types ook al zitten ze dieperliggend in geneste paragrafen.
	- De systeemnaam wordt nu correct overgenomen van de naam bij het toevoegen van een component aan een paragraaf
	- Verbetering wanneer je een eerdere keuze ongedaan maakt bij keuzelijsten.
	- De Video embed kan opnieuw gebruikt worden in een paragraaf component.
	- Broodkruimel en labels worden nu correct getoond bij gebruik van een content blok
	- Het werken met een zoekbereik is nu ook voorzien op een Adres content component. Dit was voordien enkel beschikbaar bij een Locatie content component.
	- De rollen die toegekend worden in een workflow zullen nu het bewerk icon niet overschrijven in de user interface
	- Bij het aanmaken van content is de lijst van beschikbare content types en blokken nu correct sorteerbaar.
    - De naam van een content component dat gezet wordt in een paragraaf zal correct bewaard worden
-  **Navigatie:** Glitches weggewerkt wanneer een content item in de navigatieboom geregistreerd wordt.
-  **Workflow** 
   -  Verbetering bij de selectielijst voor een status van een workflow.
   -  Het verwijderen van een status is nu mogelijk (zonder harde refresh)
   -  Transities worden geladen, ook voor gebruikers zonder de nodige rechten
-  **Rollen & Rechten:** Gebruikers die via UM een rol krijgen worden nu sneller aan De Redactie toegevoegd
-  **Site:** Success boodschap werd bij de site op de verkeerde plaats getoond
-  **Systeem:** Redactie monitor endpoint geeft nu geen errors meer


## [4.1.5]: 2022-01-10
[![Generic badge](https://img.shields.io/badge/Core-PRD-green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15735).
### Changed
-   **Algemeen:** Verbeterde copy doorheen de applicatie
-  **Content** 
	- Autocomplete bij het zoeken naar een content referentie (interne link) vlotter gemaakt. 
	- De filter op datum in het Content overzicht werkt nu op laatst bijgewerkt (ipv publicatiedatum)
	- Het verwijderen van een filter in het content overzicht werkt vlotter
	- Het invoeren van content zal iets 'rustiger' worden qua stijl (lettertype groottes worden beter afgestemd)

### Fixed
-  **API**
	- Views filteren via de API is uitgebreid, [zie hier voor de mogelijkheden](https://docs.google.com/spreadsheets/d/1pylW8fwLd0IxLAyQ7WaYRH6sbRow7xsv8lRZSUXf3-k/edit#gid=0).
	- Interne linken die gelegd worden in een Tekstvak met opmaak worden nu volwaardig door de API geleverd. 
-  **Content** 
	- Boodschap netjes gezet wanneer je een UUID kopiëert.
	- WCAG compliancy optie bij bestanden wordt nu correct gevalideerd
	- Hulpteksten van invoervelden beter uitgelijnd
	- Een content component verwijderen van een content type en daarna terug toevoegen (obv een ander content component) is verbeterd. 
    - Wanneer validatie foutboodschappen uit beeld voorkwamen zag je ze niet staan. Nu zal het systeem naar boven/onder scrollen bij het bewaren van een content en zo de fout in beeld brengen.  
    - Editeren van een component in een Paragraaf op een content type zal geen crash meer veroorzaken. (Wit scherm aka WSOD)
-  **Navigatie:** Een content item in de navigatieboom hangen is nu verbeterd voor kleinere schermen. 
-  **Rollen & Rechten** 
    -  De rollen op tenant zijn terug zichtbaar, zo kan de rol Content Beheerder opnieuw uitgedeeld worden.
    -  Gebruikers zonder een tenant rol (tenant of content beheerder), kunnen nu ook bestanden uploaden.
-  **Workflow:** Een content item met een status dat niet in de workflow voorkomt zal geen crash meer veroorzaken. (Wit scherm aka WSOD)
-  **Workflow** 
   - Je kan nu een workflow correct verwijderen op site niveau.
   - Als je een transitie maakt naar dezelfde status, bv van Werkversie naar Werkversie dan worden nu de rechten en de workflow configuratie correct nageleefd.

## [1.0.0] 2021-12-23  
[![Generic badge](https://img.shields.io/badge/Tabel%20Contrib-PRD-green.svg)]()

- De Tabel module is beschikbaar op Productie. Met deze module kan je een tabel toevoegen aan de content. Merk op dat dit een losstaande content component is en niet een onderdeel van een Tekstvak met Opmaak. Je bepaalt zelf de rijen en kolommen en geeft op wat je in elke cell wil plaatsen zoals bv een tekstvak, een telefoonnummer, etc.


## [4.1.2]: 2021-12-14 
[![Generic badge](https://img.shields.io/badge/Core-PRD-green.svg)]()

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15538).
### Added
-  **Algemeen:** Visuele feedback bij het kopiëren van een UUID
-  **Content** 
	- Nieuw content component '*Cross site content referentie*'. Laat toe om naar content items te refereren over sites heen binnen dezelfde tenant.
	- Content types kunnen nu verwijderd worden
	- Het URL patroon heeft nu een default waarde [item:slug]
	- Views verwijderen
-  **Navigatie:** Navigatie items kunnen nu vervangen worden
-  **Search:** Elasticsearch "reindex" functionaliteit voor alle content items (enkel voor antwerpen site binnen A-stad tenant)


### Changed
-  **Algemeen:** Verbetering van teksten (microcopy)
-  **API**
	- Swagger voor occurrences calls
	- Content events op kafka gebeuren nu met een kleine delay om rekening te houden met async cache invalidatie
-  **Content**
	- Statussen in filter overzicht
	- Het gedrag van de bewaar knop van een content item is bijgewerkt
	- UI voor verwijderen van content type/blok
	- Verbeterpunten voor URL patroon, oa. er is nu steeds een default patroon
	- Bevat operator binnen view voor CKEditor veld
-  **Systeem:** Server monitor calls
-  **Workflow**
	- Statussen in content overzicht en filter
	- Implementatie statussen call op site niveau

### Fixed
-  **Algemeen:** Verwijderen vanfilters op overview pagina's is verbeterd (was incosistent)
-  **API:** Sorteren van content items o.b.v een view is verbeterd
-  **Content**
	- Verwijderen van onbewaarde content items
	- De padding van een Tekstvak met opmaak (gelijkgetrokken met andere invoer velden)
	- Crop positie bij afbeeldingen
	- Positionering van de hulptekst bij een titel invoer veld
	- WCAG Compliancy behaviour binnen content component
	- Validatie alert wordt nu getoond wanneer er op opslaan geklikt wordt en er zijn validatie fouten bij de invoer van content
	- Interne link bij het zoeken naar content items is verbeterd
	- Velden met een standaard waarde kunnen niet meer gewist worden
	- Conflicterende (= gelijke) namen tussen oude en nieuwe content componenten veroorzaakt foutieve validatie, data van oude, verwijderde content component "X" van type Y wordt geprojecteerd op nieuw toegevoegde content component "X" van type Z
	- Opslaan van preview settings voor een site
-  **Navigatie:** Na het publiceren van een content item wordt de status van het navigatie item meteen aangepast
-  **Workflow**
	- Bewaren van content item in zijn huidige status, ongeacht de ingestelde workflow geeft nu correcte info weer
	- Ophalen van site rollen is verbeterd (gaf soms een 403)
	- Als gebruiker met de "workflow update" rechten kan je nu de instellingen van een workflow bewerken

## Legende
De release notes zijn chronologisch gesorteerd met de meeste recente release eerst. De badges geven aan over welk onderdeel het gaan en in welk stadia het zich bevindt. 
- [![Generic badge](https://img.shields.io/badge/Core|Contrib-gray.svg)]() Gaat de release over de core of over een contributie module.
- [![Generic badge](https://img.shields.io/badge/Core|Contrib-TODO-teal.svg)]() zijn alle features die gaan ontwikkeld worden. 
- [![Generic badge](https://img.shields.io/badge/Core|Contrib-DEV-yellow.svg)]() zijn alle features die momenteel ontwikkeld worden en nog niet beschikbaar zijn.
- [![Generic badge](https://img.shields.io/badge/Core|Contrib-ACC-blue.svg)]() zijn alle features die we momenteel aan't testen zijn. Deze zullen weldra gereleased worden.
- [![Generic badge](https://img.shields.io/badge/Core|Contrib-PRD-green.svg)]() zijn alle features die gereleased zijn voor gebruik.

*The formaat is gebaseerd op [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), en maakt gebruik van [Semantic Versioning](https://semver.org/spec/v2.0.0.html).* 

## Vragen?
De releases worden op basis van een lange termijn en korte termijn planning samengesteld op basis van de behoefte van de afnemers van het platform. Staat er iets niet tussen of heb je een vraag over de release notes? contacteer dan erik.lenaerts@digipolis.be
