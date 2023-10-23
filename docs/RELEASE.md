# Release notes

Hier vind je de release notes van **GPubP - Content beheer** (aka **De Redactie**, aka **WCMv4**), één van de onderdelen van het [Generiek Publicatie Platform](/README.md).

*Lees [hier meer](#legende) over het formaat en de structuur van deze release notes.*

## Index

| Release | Release Datum | Inhoud | Status |
|---|---|---|---|
| [4.10.0](#_4100) | Q4 2023 | Navigation v2 | [![Generic badge](https://img.shields.io/badge/Core-TODO-teal.svg)]() |
| [4.9.0](#_490) | Q4 2023 | Backup & restore van structuren | [![Generic badge](https://img.shields.io/badge/Core-DEV-yellow.svg)]() |
| [4.8.4](#_484-2023-11) | Nov 2023 | Technische upgrade ikv Move To Orange - deel II | [![Generic badge](https://img.shields.io/badge/Core-TODO-teal.svg)]() |
| [4.8.3](#_483-2023-11) | Nov 2023 | Solr afbouw + bug fixes (deel II) | [![Generic badge](https://img.shields.io/badge/Core-TODO-teal.svg)]() |
| [4.8.2](#_482-2023-11) | Nov 2023 | GIS module v2 | [![Generic badge](https://img.shields.io/badge/Core-DEV-yellow.svg)]() |
| [4.8.1](#_481-2023-10) | Okt 2023 | Technische upgrade ikv Move To Orange | [![Generic badge](https://img.shields.io/badge/Core-DEV-yellow.svg)]() |
| [4.7.3](#_473-2023-08-31) | 23 aug 2023 | Solr afbouw + bug fixes (deel I) | [![Generic badge](https://img.shields.io/badge/Core-DEV-yellow.svg)]() |
| [4.7.2.hotfix-1](#_472hotfix-1-2023-07-06) | 6 jul 2023 | fix voor ophalen taxonomy termen | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.7.2](#_472-2023-02-07) | 7 feb 2023 | Logboek v1, Nieuwsbrief v1.1 en Event module v1.1 | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.7.1](#_471-2023-02-07) | 7 feb 2023 | Focus en Ken burns afbeelding effecten + bug fixes | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.7.0](#_470-2022-11-09) | 9 nov 2022 | WCM Event module | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.6.5](#_465-2022-11-02) | 2 nov 2022 | Broadcast module voor o.a. nieuwsbrieven | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.6.0.hotfix-1](#_460hotfix-1-2022-10-24) | 24 okt 2022 | Performantie fix en data migratie verbetering | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.6.0](#_460-2022-10-18) | 18 okt 2022 | Standaard ondersteuning & integratie met Elastic App Search | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.5.1](#_451-2022-08-04) | 4 aug 2022 | Bijkomende release voor BRaaS en bugfixes van 4.5 | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [1.0.0](#_100-2022-07-07) | 7 jul 2022 | Bynder Beeldenbank en Chat ondersteuning | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.5.0](#_450-2022-07-07) | 7 jul 2022 | Verbeterde werking met BRaaS | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.4.1](#_441-2022-07-07) | 7 jul 2022 | Bijkomende release met bugfixes van 4.3 & 4.4 | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [1.2.0](#_120-2022-06-23) | 23 jun 2022 | Tabel content component aanpassingen | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.4.0](#_440-2022-06-23) | 23 jun 2022 | Meertaligheid | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.3.0](#_430-2022-06-23) | 23 jun 2022 | Werken met Navigatie Menu's, URL patronen en sitestructuren | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1.hotfix-6](#_421hotfix-6-2022-04-14) | 14 april 2022 | Noodzakelijke fixes op productie | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1.hotfix-5](#_421hotfix-5-2022-03-24) | 24 maart 2022 | Noodzakelijke fixes op productie | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1.hotfix-4](#_421hotfix-4-2022-03-10) | 10 maart 2022 | Noodzakelijke fixes op productie | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1.hotfix-3](#_421hotfix-3-2022-03-03) | 03 maart 2022 | Noodzakelijke fixes op productie | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1.hotfix-2](#_421hotfix-2-2022-02-24) | 24 feb 2022 | Enkele fixes rond uitgifte tijdstip (PZA) | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1.hotfix-1](#_421hotfix-1-2022-02-17) | 17 feb 2022 | Fix voor werken met 10+ navigatiebomen | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.2.1](#_421-2022-02-14) | 14 feb 2022 | Uitbreidingen voor PZA | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [4.1.5](#_415-2022-01-10) | 10 jan 2022 | Rubens release voor A-Stad | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |
| [1.0.0](#_100-2021-12-23) | 23 jan 2022 | Tabel content component | [![Generic badge](https://img.shields.io/badge/Contrib-PROD-green.svg)]() |
| [4.1.2](#_412-2021-12-14) | 14 dec 2021 | MVP Release | [![Generic badge](https://img.shields.io/badge/Core-PROD-green.svg)]() |

---
## Legende
### Badges
De release notes zijn chronologisch gesorteerd met de meeste recente release eerst. De badges geven aan over welk onderdeel het gaan en in welk stadia het zich bevindt. 

| Badge                                                                             | Omschrijving                                                                                 |
|:----------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------|
| [![Generic badge](https://img.shields.io/badge/Core_\|_Contrib-gray.svg)]()       | Gaat de release over de core of over een contributie module.                                 |
| [![Generic badge](https://img.shields.io/badge/Core_\|_Contrib-TODO-teal.svg)]()  | zijn alle features die gaan ontwikkeld worden.                                               |
| [![Generic badge](https://img.shields.io/badge/Core_\|_Contrib-DEV-yellow.svg)]() | zijn alle features die momenteel ontwikkeld worden en nog niet beschikbaar zijn.             |
| [![Generic badge](https://img.shields.io/badge/Core_\|_Contrib-ACC-blue.svg)]()   | zijn alle features die we momenteel aan't testen zijn. Deze zullen weldra gereleased worden. |
| [![Generic badge](https://img.shields.io/badge/Core_\|_Contrib-PRD-green.svg)]()  | zijn alle features die gereleased zijn voor gebruik.                                         |

*The formaat is gebaseerd op [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), en maakt gebruik van [Semantic Versioning](https://semver.org/spec/v2.0.0.html).* 

### Release vs Hotfix
Bij een **release** worden alle zaken die momenteel ontwikkeld zijn - zowel features, changes als bugfixes - meegenomen en gedeployed.

Bij een **hotfix** worden heel specifieke user stories geselecteerd en enkel die gedeployed. Alle andere zaken die reeds klaar waren, worden dus niet mee gedeployed. 

 
## [4.9.0]

**Visie:** Deze release laat toe om structuur te backupen en in een andere tenant te restoren. 

[Terug naar het overzicht](#_index)

## [4.8.1]: 2023-10

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16911)

De MTP in oranje zal gefaseerd gaan volgens onderstaand release schedule:

| Release | Fase | MTP datum (2023)  | Impact op afnemers | Impact op Redacteurs |
|---|---|---|---|---|
| 4.8.1.a | voorbereiding (geen deploy) | 27 oktober  09:00 uur | geen | geen |
| 4.8.1.b | Niet kritieke services | 31 oktober 09:00 uur  | geen | downtime 2 à 3 minuten. Bynder: Geen afbeeldingen uit bynder kunnen halen Forms: Geen nieuwe form referenties kunnen leggen in content |
| 4.8.1.c | Navigatie & taxonomy | 2 november 09:00 uur  | downtime 2 à 3 minuten geen taxonomie en navigatie data 	ophalen/bewerken recovery 1 uur   | downtime 2 à 3 minuten redactie onbeschikbaar recovery 1 uur   |
| 4.8.1.d | Assets & translations | 7 november 09:00 uur  | downtime 2 à 3 minuten geen afbeeldingen en bijlagen kunnen ophalen recovery 1 uur | downtime 2 à 3 minuten redactie onbeschikbaar recovery 1 uur   |
| 4.8.1.e | Content | 8 november 09:00 uur  | downtime 2 à 3 minuten geen content kunnen ophalen recovery 1 uur | downtime 2 à 3 minuten redactie onbeschikbaar recovery 1 uur   |
| 4.8.1.f | Workflow & Sites | 9 november 09:00 uur  | downtime 2 à 3 minuten geen content kunnen ophalen recovery 1 uur | downtime 2 à 3 minuten redactie onbeschikbaar recovery 1 uur   |
| 4.8.1.g | Search & Sockets  | 14 november 09:00 uur  | geen | downtime 2 à 3 minuten geen nieuwe search inrichtingen kunnen opzetten mogelijks herindexatie nodig recovery 1 uur   |
| 4.8.1.h | BRaaS | 15 november 09:00 uur  | geen | downtime 2 à 3 minuten mogelijks Not Allowed Errors Na de switch best opnieuw aanmelden recovery 1 uur   |
| 4.8.1.i | Core services | 16 november 09:00 uur  | downtime 2 à 3 minuten geen taxonomie, navigatie data, content, afbeeldingen, bijlagen ophalen/bewerken recovery 1 uur   | downtime 2 à 3 minuten redactie onbeschikbaar recovery 1 uur   |
| 4.8.1.j | Yapla modules | 21 november 09:00 uur  | TBD | TBD |
| 4.8.1.k | Redactie UI | TBD | geen | TBD  |



### Changed
* alle services zijn gereviewed en aangepast zodat ze werken met de laatste nieuwe versie van programeertalen, frameworks en dependencies. 
* het reduceren van de payload bij het ophalen van content via de WCM API is aangepast
    > [!attention|label:Breaking change]
    > Als je zowel parent als child objecten filtert in de request zal er nu enkel de child content terugkomen in de payload. [Je kan hier de details bekijken](/wcmv4/content/content-payload?id=filter-voorrang-regels).

### Fixed
- **API** 
  - Als API afnemer krijg ik geen gearchiveerde content items meer bij het ophalen van content
  - Als API afnemer krijg ik terug `alle diensten` door middel van de API call met populatie. 

- **Content**
  - het maken van grotere en complexere Content Types is verbeterd.
  - Gearchiveerde content items kan je niet meer ophalen via de reguliere WCM Content API calls
  - Als cCntent beheerder kan ik opnieuw Content Componenten aanmaken
  - Als Content beheerder kan ik opnieuw werken met workflows
  - Als Redacteur zie ik terug de velden Titel en omschrijving van de OG en Meta data secties 
  - Als redacteur lukt het terug om content blokken aan te maken

[Terug naar het overzicht](#_index)

## [4.7.4]: 2023-09

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16705)

### Added
- **Search** 
  - Als redacteur kan ik kiezen, per content item, om deze niet mee op te nemen in één of meerdere indexen van Elastic Search
  - Als site beheerder kan ik voor een content blok een content referentie opgeven wat de basis vormt voor de url.

### Fixed
- **Content**
  - Publiceren bij een mislukte geplande publicatie is hersteld
  - De vuilbak iconen komen nu niet meer voor bij de opmaak van een content referentie en een link.
- **Search** 
  - Indexering van een site in het nederlands creëert geen engines meer voor de andere talen van de tenant

## [4.7.3]: 2023-08-31

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16705)

### Added
### Fixed
- **Content**
  - Geen dubbele hulpteksten meer bij Teksvak met opmaak
- **Meertaligheid**
  - de alt-tekst van een afbeelding vloeit niet meer van één content item naar een ander in geval er in meerdere talen content wordt ingegeven. 
- **Search** 
  - verwijderde content wordt nu ook uit elastic verwijderd.
  - gearchiveerde content worden nu uit elastic verwijderd, ook bij een herindexering.

## [4.7.2.hotfix-1]: 2023-07-06
### Added
- **API:** Je kan nu de term data ophalen van een taxonomy zonder dat je de `taxonomyId` moet meegeven (enkel `termId`)

## [4.7.2]: 2023-02-07

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16432)

### Added
- **Event module**
  - Nieuwe versie van de WCM Event module met ondersteuning voor async API documentatie

- **Logboek module**
  - Er is een logboek dat de verzendgebeurtenissen weergeeft. 
  - Het logboek kan ook door andere modules gebruikt worden in het systeem om zo een goe beeld te krijgen wat en wanneer er allemaal gebeurt. 
  - Het logboek kan een handig hulpmiddel zijn voor troubleshooting. 

- **Broadcasting module**
  - todo

### Fixed

[Terug naar het overzicht](#_index)

## [4.7.1]: 2023-02-07

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16431)

### Added
- **Afbeeldingen**
  - Als gebruiker kan je nu naast een crop ook een focus area aangeven. Deze kunnen door frontends gebruikt worden om de focus zone in beeld te houden bij de verschillende device form factors.
  - Je kan een Ken Burns effect zetten op een afbeelding waar je ofwel in - of uitzoomt.

- **Content**
  - Het systeem zal aangeven wanneer je het maximum aantal tekens hebt bereikt bij het invoeren van tekst in een tekstvak (met of zonder opmaak).

### Changed
- **Content** 
  - De slug van content items worden nu via een ander algoritme gegenereerd (van KebabCase naar Slugify)
  - De content type referentie component heeft nu ook een multiple optie

- **Rollen en Rechten:** Door een gebrek aan paging in BRaaS kon de redactie slechts 50 gebruikers tonen. Dit is opgetrokken tot 100. 

### Fixed
- **API** 
  - Je kon onterecht via de API gearchiveerde content ophalen indien je `populate=true` meegaf.
  - het `meta.urlPath` wordt correct bijgewerkt indien deze automatisch door de Redactie is aangepast
  
- **Content**
  - Wanneer de slug manueel wordt aangepast zal het systeem de slug (opnieuw) veilig maken voor gebruik in een URL. Zo zullen blanco's bv vervangen worden door een `-`. De redactie zal in deze gevallen een melding aan de redacteur tonen.
  - De bewaarknop is terug in orde en wordt terug actief na het bewerken van crops van een afbeelding.
  - De tijden zijn nu verplicht bij het invoeren van een vaste periode.
  - Tijdslot content component geeft nu het correct aantal tijdsloten weer dat er gegenereerd gaat worden volgens een ingesteld herhaal patroon.
  - De bewaar knop bleef actief na een bewaar actie voor sommige content items.
  - Een content type referentie component behoud nu correct z'n ingestelde waarde door de redacteur.
  - Doel en opmaak instellingen bij een content referentie tonen geen vuilbak icons meer voor de redacteur
  - Overzicht van revisies toont terug de twee geselecteerde revisies als je van de vergelijkenpagina terugkeert naar het overzicht.
  - De redactie toonde soms dubbele tooltips, een blauwe van het redactie systeem en daarbovenop een zwarte die de browser zelf (op safari) voorzag.

- **Search**
  - Bij het herindexeren van grote sites loopt het systeem niet meer vast
- **Navigatie**
  - De leave popup wordt niet meer getoond van een net bewaard content item als je naar het sitestructuur compartiment gaat.
  - Context popup van een content item laad correct als je dit opvraag vanuit de sitestructuur

- **Wiews:** Bij het tonen van de voorbeeld inhoud van een view werkt de paginering nu correct. 
- **Workflow:** Een custom status wordt nu correct gepresenteerd in de redactie en niet meer als `werkversie`.

[Terug naar het overzicht](#_index)

## [4.7.0]: 2022-11-09

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16228)

### Added
- **Events**
  - De WCM Event Module laat toe om bepaalde interne gebeurtenissen in de WCM op de Event handler te zetten zodat afnemers hierop kunnen reageren. Content beheerders kunnen heel fijnmazig afstellen welke events er zo naar buiten toe ontsloten worden.
  - Als content beheerder kan ik aangeven op welke namespaces er mag afgeleverd worden van de Event Handler
  - Als content beheerder kan ik een aflevering configureren en aangeven welk intern event afgeleverd mag worden
  - Als content beheerder kan ik extra filters instellen bij een event aflevering, zo kan je nog fijnmaziger inrichten welke events afgeleverd mogen worden. bv enkel van site x, of voor content type y, etc
  - Als content beheerder kan ik een test event versturen om de integratie ketting te testen
  
### Fixed
- **Navigatie**
  - Het Content type word nu opgekuist uit het sitestructuur overzicht van zodra de configuratie aangepast wordt 
  - Het Content type kwam in bepaalde scenario's teveel voor in de sitestructuur
  - Een Content item wordt nu opgekuist uit het sitestructuur overzicht wanneer het niet meer in de sitestructuur wordt gehangen
  - Alle navigatiebomen zijn beschikbaar als een content item bewerkt wordt

- **Meertaligheid:** Meta informatie wordt correct overgenomen bij het maken van een vertaling van een content item.

[Terug naar het overzicht](#_index)

## [4.6.5]: 2022-11-02

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16423)

### Added
- **Broadcast module** 
  - De broadcast module laat toe om content af ergens af te leveren. Ingeval van PZA het nieuwsbriefsysteem.
  - Als content beheerder kan je verschillende verzendkanalen opzetten
  - Per kanaal wordt bepaalt welke content er waar moet afgeleverd worden.
  - SendGrid (e-mail campagne systeem) is de eerste aflevermethode. het systeem voorziet dat andere methodes ingeplugd kunnen worden.
  - Er kan ad hoc, één per één en in bulk verstuurd worden al dan niet time of volume gebaseerd.
  

### Fixed
- **API** 
  - De HTTP header `cache-control: no-cache` zal nu altijd de actuele data ophalen, ook al wordt er gepopuleerd. Bij gebruik van deze HTTP cache header kan een API call trager gaan omdat de cache opnieuw opgebouwd moet worden voor dit content item.
  - Een zoekindex referentie zal nu de naam van de elastic engine terugsturen in plaats van de uuid
    > [!attention|label:Breaking change]
    > ```json
    > {
    >   "_id": "6352c402f0b7a10007ced26a",
    >   "fields": {
    >       "zoekindex": "wcm-algemeen-werk-in-kaart-tenant-test-5-acceptance"
    >   },
    >   "uuid": "bb6d59f2-5072-4a86-ae5c-bfab0b1a5930"
    > }
    > ```
- **Content** 
  - Het verwijderen van een link in een tekstvak met opmaak tas de andere linken in dezelfde alinea niet meer aan
  - Wanneer je een content item archiveerd zullen ook de wijzigingen die je aanbracht mee bewaard worden.
  - Linken in content die geplakt is in het tekstvak met opmaak kan je nu bewerken.
  - Externe linken mogen nu ook met http:// starten (voordien enkel https://)
  - Uitgiftedatum wordt nu correct gezet, ook al als je meteen een nieuwe content item publiceert
  - Uitgitedatum wordt correct bijgewerkt op basis van de laatste publicatiedatum (indien het zo is ingesteld op het content type). 
  - Ingave van start en/of einduur gaat niet meer crashen op Safari
- **Search** 
  - Een reeks verbeteringen voor de indexering van data gebaseerd op het Tijdslot en Vaste periode content component
  - Content indexering gaat nu kijken naar de site url zodat anderstalige content de juiste basis hebben voor hun linken
  - De vooruitgang wordt nu correct getoont bij de indexatie
  - De rechten rond herindexatie worden nu correct afgedwongen
- **Navigatie**
  - Nieuwe content types hebben nu een default URL patroon 
  - modulesData is verwijderd uit het content item
    > [!attention|label:Breaking change]
    > Alle afnemers die nog gebruik maken van de modulesData om de link naar de navigatienode op te zoeken gaan deze info niet meer terugvinden op het content item. 
    > Let op, dit is enkel ingeval je gebruik maakt van de nieuwe navigatie module uit release v4.3
    > In deze nieuwe aanpak ligt de link andersom, vanuit de navigatienode kan je de link vinden naar het content item.
  


[Terug naar het overzicht](#_index)

## [4.6.0.hotfix-1]: 2022-10-24

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16424)

### Fixed
- **Content** 
  - Performantie verbeteringen van de Redactie UI
  - Een extra functie dat is toegevoegd ter ondersteuning van data migratie scripts. Deze functie heeft geen impact op de WCMv4 API of de Redactie UI.

[Terug naar het overzicht](#_index)

## [4.6.0]: 2022-10-18

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15730)

### Added
- **Search** 
  - Als Tenant beheerder kan ik de Search Module activeren voor m’n tenant
  - Als Tenant beheerder kan ik bepalen met welke Elastic App Search installaties er gewerkt kan worden (hun endpoints beheren). ie. Er kan een on-prem of cloud installatie zijn, Stad en PZA kunnen op een andere installatie werken, etc). Meerdere installaties kunnen gedefinieerd worden
  - Site beheerders kunnen ‘Search’ activeren en kunnen aangeven op welke installatie ze gaan werken
  - Site beheerders kunnen per selectie van content types aangeven in welke index (=engine) dit moet terechtkomen. Zo kunnen we alle content in één index zetten, of à la limit voor elk content type een aparte index opgeven. Hierbij kunnen content types meerdere keren voorkomen in andere indexen. Het is dus een M/N relatie tussen content types en indexen
  - Site/Content beheerders kunnen de mapping eenvoudig beheren van de componenten van een content type naar de velden van het schema van een elastic app engine. De wijze hoe data overgezet wordt ligt vast (hier en hier beschreven), maar wat er waar naar gemapped wordt is dus aanpasbaar. 
  - De bestaande indexering mapping logica, specifiek voor gemaakt voor A-Stad 2.0, is overgenomen. Deze bevat de generieke wijze hoe content componenten gemapped zijn naar schema velden van een Elastic App Search engine.
  - Als Site/Content beheerder kan ik bepalen welke afbeeldingen mee geïndexeerd moeten worden. 
  - Het systeem (her-)indexeert automatisch bij verandering van taxonomie labels uit de taxonomy engine en/of content uit de WCMv4. 
  - Als Sitebeheerder kan ik zelf on-demand een volledige of partiële herindexering starten van content en taxonomie gegevens. Hierbij krijg ik visueel feedback 
  - Het verloop van indexering kan gevolgd worden dmv standaard logging.
  - Er is een nieuw zoekindex referentie content component
  - Er is een nieuw zoekindex veld referentie content component
- **Content**
  - Er kan een maximum aantal tekens ingesteld worden bij tekstvakken
  - ingeval een slug al in gebruik is wordt er automatisch een opvolgingsnummer aan toegevoegd
  - Alle nieuwe content types gaan standaard een tekstvak met opmaak gebruiken als teaser component.
  - Er is een nieuw nummerbereik content comoponent
  - Er is een nieuw tijdbereik content comoponent
- **Configuratie**
  - Er is een generieke aanpak om instellingen op tenant niveau te organiseren (ook voor contrib modules)
  - Er is een generieke aanpak om instellingen op site niveau te organiseren (ook voor contrib modules)
- **Monitoring:** APM instellingen zijn bijgewerkt
- **Views:** Views kunnen nu gefilterd worden op uitgifte tijdstip

### Changed
- **API** 
  - Enkele verbeteringen voor het beheren van taxonomieëen waaronder
    - positie informatie komt eenduidiger uit de API
    - PUT /terms is op deprecated gezet, in de plaats is nu een functie om termen te ordenen
    - Elke term kan nu gebruik maken van een externalRef property
    - De PUT van een /term is opgekuist en je hoeft geen meta data meer mee te geven
    - property waarden kunnen nu zowel bij een POST als PUT van een term worden meegegeven
  - Tijdslot (vroegere tijdstip) content component geeft nu een ISO date terug
    > [!danger|label:Breaking change]
    > *Het tijdstip contont component gaat nu een ISO date zonder tijdsaanduiding terug geven
    > ```json
    > "startDate": "2021-12-12T23:00:00Z" --> '2021-12-12' 
    >```
  - De API geeft nu alle Datetime data terug in UTC. 
    > [!danger|label:Breaking change]
    > Controleer als afnemer dat je datetime info correct als UTC interpreteert en niet als lokale BRU tijd.
  - afnemers kunnen nu op aanvraag wachten op de meest actuele data. Zonder kan het zjin dat ze nog een oude versie terug krijgen terwijl de cache nog volop aan't bijwerken is.
    > [!warning|label:Wijziging in caching behaviour]
    > gebruik hiervoor de volgende HTTP Header
    > ```bash
    > GET /v1/sites/{siteId}/content?slug=xyz&lang=nl
    > --header 'Cache-Control: no-cache'
    >```
- **Content** 
  - redacteurs kunnen nu 3 verschillende YouTube url varianten plakken in de Video embed content component. De API zal steeds de embed variant teruggeven.
  - Content beheerders kunnnen nu van alle structuurelementen (content types, componenten, blokken, taxonomie,...) de systeemnaam zien in de Redactie. 
  - Datum Tijd content component is vernieuwd met een betere ingave voor redacteurs
  - Tijdslot (vroegere tijdstip) content component is vernieuwd met een betere ingave voor redacteurs
  - Er is een verbeterde Taxonomy Referentie content component
  - Er is een verbeterde Content Type Referentie content component
  - voor A-Stad is de maximale bestandsgrootte verhoogd naar 10MB van uploadqs
- **Navigatie** 
  - enkele verbetering voor het werken met de navigatie structuren waaronder 
    - externalRef komt mee bij het ophalen van broodkruimels
    - beschrijving is niet meer verplicht voor redacteurs bij het plaasen van content in de sitestructuur
    - de kinderen in een sitestructuur worden nu wel goed gepresenteert
    - self healing sitestructuur ingeval er één ontbreekt
- **Search:** tijdslot (het vroegere tijdstip) heeft een specifieke indexeringswijze (zowel in de MVP als definitieve oplossing)
   
### Fixed
- **API** 
  - Je kan nu een view filteren op basis van gerelateerde data.
  - Je kan een view filteren op uitgifte tijdstip (issuedOn)
  - Je kan nu meta data correct uitsluiten uit de API responses
  - Je kan nu data filteren in een view op basis van gerelateerde (populated) data. 
- **Content**
  - Bij het synchroniseren van een afbeelding wordt de metadata in correcte taal ingeladen
  - De video embed validatie blokkeert het bewaren van het content item niet meer.
  - De naam van de import applicatie wordt nu correct weergegeven in de Redactie
  - Het dubbele tijdstip content component is nu verdwenen
  - Tijd component verplicht maken resulteerd niet meer in een WSOD
  - Er wordt geen URL meer getoond in het content item overzicht voor content blokken
  - De vertaal tab is niet meer aanwezig voor content items van sites met één taal.
  - De broodkruimel van applicatie accounts is goed gezet
  - Als content beheerder kan je terug de lijst van content types zien bij het gebruik van een content referentie content component
  - Als redacteur kan je nu correct de taxonomie referentie gebruiken bij de inrichting van search filters
  - De dubbele 'gearchiveerd' status voor de PZA tenant is verdwenen
  - vertaal tab is weg bij het bewerken van een content item voor ééntalige sites
  - het home-segment van de broodkruimel in de Redactie is op enkele plekken goed gezet
  - Content dat via de API is gemaakt staat nu onder de juiste naam van de auteur, i.e. de toepassing die de content maakte.
  - het plannen van publicaties van nieuwe en gerecycleerde content items is opgelost
  - View referenties in een content item kunnen nu verwijderd worden 
  - Datums worden correct weergegeven wanneer men een content item bekijkt
  - In het content overzicht wordt de taalfilter ook gereset wanneer men de actie 'Alles leegmaken' kiest
  - Content types kunnen nu geactiveerd worden voor Sites waar al veel content aanwezig is 


[Terug naar het overzicht](#_index)

## [4.5.1]: 2022-08-04

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16308)

### Fixed
- **API**: Filteren op taxonomieën via views is verbeterd.
- **Navigatie:** interne linken die gelegd worden in een tekstvak met opmaak worden nu relatief bewaard in de content en absoluut in Elastic. 
- **Media** 
  - Validate bij invoer van meerdere bestanden is verbeterd
  - Beelden kunnen nu hergebruikt worden indien ze voldoen aan de dimensievoorwaarden
- **Meertaligheid**
  - Elk content item bevat nu de url's naar de beshcikbare vertalingen ervan
  - Preview url's worden correct opgebouwd in alle talen
- **Workflow** Er werd meteen gepubliceerd in plaats van éérst een werkversie te maken bij het bewaren van een content item

[Terug naar het overzicht](#_index)

## [1.0.0]: 2022-07-07

- WCM Bynder Module: Beelden uit [Bynder](https://www.bynder.com/) kunnen gekozen worden door de redacteur rechtstreeks uit de Redactie.
- Je kan zoeken op een term of op een id van een beeld in Bynder
- De gekozen afbeelding wordt geïmporteerd in de WCM, alsook de meta dat
- [Teleportel](https://www.teleportel.com/) ondersteuning


[Terug naar het overzicht](#_index)

# [4.5.0]: 2022-07-07

[Terug naar het overzicht](#_index)

### Added
Deze release gaat de werking met BRaaS zo goed mogelijk stabiliseren, concreet: 
- Bij het bewaren van rechten worden extra controles uitgevoerd of deze acties effectief uitgevoerd zijn of niet
- APM ofwel Application Performance Monitoring wordt ingebouwd
- Bij het rollen en rechtenscherm wordt de header vastgeklikt zodat het makkelijk is om rechten te zetten voor de juiste rol
- Bij het rollen en rechtenscherm worden bij het aanklikken van individule compartimenten de rechten sneller geladen
- Bij het rollen en rechtenscherm worden bij alle aanpassingen in de individuele compartimenten samen genomen bij het bewaren

[Terug naar het overzicht](#_index)

## [4.4.1]: 2022-07-07

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16242)

Extra release voor bugfixes van versie 4.3 & 4.4.
### Added
- Content wordt geïndexeerd in Elastic per taal in een aparte index/engine
- Meta data wordt automatisch mee geïndexeerd in Elastic
- Datums van een activiteit worden in een apart veld geïndexeerd
- Betere default values voor werken met multilanguage sites
- verbeterde weergave van de revisies 

### Fixed
- Punten van nieuwe GIS lagen komen nu wel door
- verbeteringen in het filteren van views
- Gearchiveerde / offline pagina's kan je niet ophalen via de API
- Herindexeren geeft geen HTTP 500 fout meer
- Taxonomy termen staan nu in de keuzelijst in dezeflde volgorde als in de taxonomy
- Het aantal content items per taal wordt correct weergegeven in het overzicht 

[Terug naar het overzicht](#_index)

## [1.2.0]: 2022-06-23

De tabel content component is aangepast met:

[Terug naar het overzicht](#_index)

## [4.4.0]: 2022-06-23

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15729).

### Added
  - Per site configureer je de talen
  - Allerlei instellingen zoals de site url, preview url gaan taalgevoelig worden
  - Content beheerders bepalen welke content componenten van een content type vertaalbaar zijn en welke niet.
  - Redacteurs werken aan content voor een specifieke taal. 
  - Een content item wordt gemaakt in een bepaalde taal. Heb je 4 vertalingen, dan zijn dit 4 content items
  - Er komt een taalaaduiding in het content overzicht
  - Bij het maken van een nieuw content item moet eerst nog een taalkeuze gemaakt worden.
  - Per content item kan je eenvoudig zien in welke talen dit reeds vertaald is.

[Terug naar het overzicht](#_index)

## [4.3.0]: 2022-06-23

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15728).

### Added
- **Navigatie:** 
  - Site beheerders kunnen het `URL patroon` van een content type `instellen op site niveau`, zo kan dit anders ingericht worden per site. 
    > [!warning|label:Nota voor afnemers]
    > *We nemen standaard het URL patroon over van wat er ingesteld is op tenant niveau van elk content type*.
  - Er kan gewerkt worden met `URL patroon variabele` voor de opbouw van een URL
  - Ontwikkelaars zullen nooit meer URL's moeten samenstellen in code. De URL's zijn onderdeel van elk content item.
    > [!warning|label:Nota voor afnemers]
  	> *Je kan nu URL patronen veel dynamischer instellen. Kijk de code na en verwijder alle hardcoded regels rond het opbouwen/samenstellen van een URL in de frontend code*.
  - Bij het wijzgingen van een URL patroon, kan je `in bulk` alle content items `bijwerken naar dit nieuw URL patroon`.
  - Als Redacteur kan je het pad (gedeelte voor de slug) aanpassen als je hiervoor rechten hebt. Zo kan je `afwijken van het vooropgestelde URL Patroon` voor je content item.
  - Via een Feature toggle kan je de `Menu feature de/activeren` voor je site
  - Via de API kan ik `alle informatie van een menu opvragen` voor een site
    > [!attention|label:Breaking change]
	  > *Menu's werden hiervoor beheerd in de Navigation UI. Op aanvraag kunnen we je bestaande menu's migreren zodat ze vanaf nu vanuit de redactie kunnen beheerd worden.*
	  > *Voor frontend developers is het belangrijkste dat er **geen** navigatie data meer zal bestaan op content items*.
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
    > [!warning|label:Nota voor afnemers]
  	> *Redacteurs konden content items in de navigatiestructuur plaatsen voordien. Dit is nu vervangen door uitgebreidere sitestructuur features*
  - Via de API kan ik `alle informatie van een sitestructuur opvragen` voor een site. Hier kan je alle onderliggende items in een structuur opvragen dat dikwijls gebruikt wordt bij overzichtspagina's voor het tonen van de 'child' pagina's. Anderzijds kan je ook alle bovenliggende elementen in de sitestrucuur opvragen voor bijvoorbeeld het opbouwen van een broodkruimel.
    > [!attention|label:Breaking change]
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

[Terug naar het overzicht](#_index)

## [4.2.1.hotfix-6]: 2022-04-14

### Fixed
- het verwijderen van een navigatie item volgt de nieuwe werkwijze van de recent aangepast navigatie engine ([zie Digipolis nieuws](https://nieuws.digipolis.be/project/46359))

[Terug naar het overzicht](#_index)

## [4.2.1.hotfix-5]: 2022-03-14

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15801).
### Fixed
- **Content:** De cache zal sneller worden opgebouwd waardoor er minder 'oeps, pagina niet gevonden' zal voorkomen
- **Navigatie:** enkele kleinere fixes rond het gebruik van de navigatie engine

[Terug naar het overzicht](#_index)

## [4.2.1.hotfix-4]: 2022-03-10

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15793).
### Added
- **Navigatie:** Aanpassing waarbij we eenvoudig (tijdelijk) de navigatiestructuur voor A-Stad van Acc naar Prd kunnen overzetten

### Fixed
- **Content**
  - Automatisch starten bij video component is gefixed
  - Pagina's kunnen opnieuw worden aangemaakt in de redactie
  - Transities worden nu ook geladen voor gebruiker die enkel workflow read-rechten hebben


[Terug naar het overzicht](#_index)

## [4.2.1.hotfix-3]: 2022-03-03

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15792).
### Added

### Fixed
- **Content** 
  - Views kunnen nu correct gefiltered worden obv taxonomie term(en)
  - Het gekozen adres (via de location picker) wordt nu correct bewaard in de redactie
  - Instellingen van de voorvertoning module worden nu correct bewaard

[Terug naar het overzicht](#_index)

## [4.2.1.hotfix-2]: 2022-02-24

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15788).
### Fixed
- **API:** Fix die het duidelijker maakt wanneer een content item gelocked is door een redacteur in de Redactie
- **Content** 
  - De uitgifte datum van een content item kan ondanks het veld readonly is, toch leeggemaakt worden. 
  - De uitgifte datum wordt niet aangepast aan de laatste publicatiedatum, ook al is dit zo geconfigureerd
- **Preview:** Fix waarbij de preview instelling op site niveau niet correct bewaard werd

---

[Terug naar het overzicht](#_index)

## [4.2.1.hotfix-1]: 2022-02-17

-  **Navigatie:** Er is een issue ontdekt waarbij redacteurs hun navigatieboom niet meer kunnen kiezen in de keuzelijst. De dropdown toont enkel de eerste 10 entries. We gaan hier in de hotfix zorgen dat er 20 items opgehaald worden, een betere oplossing staat op de backlog weliswaar. Hiermee kunnen de afnemers vandaag meteen verder.  


[Terug naar het overzicht](#_index)

## [4.2.1]: 2022-02-14

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15727).
### Added
-  **API** 
   -  Content schrijven kan via de WCM Content Manager API op [deze manier](https://docs.google.com/document/d/1cMGpDkgqBnVhzlr7nr00YK8xciIESvIX1YmffqT6VzE/edit#heading=h.xhcpij33fl32).
   -  Bij gebruik van een paragraaf zal er in de payload (meta) van een Content Item een `componentType` en `componentName` uitkomen die respectievelijk het type en de systeemnaam van dat Content Component in de paragraaf bevat.
-  **Content** 
	- Extra configuratie opties voor een `Tekstvak met Opmaak`. Je kan nu bepalen of er met afbeeldingen of interne linken gewerkt mag worden. ([Meer info](https://docs.google.com/document/d/19RHSpMWIhUoD4ST7d4fvd1Z-mqxb14shNrsly_mDGs4/edit#heading=h.i6gktat17chj))
    > [!warning|label:Nota voor afnemers]
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


[Terug naar het overzicht](#_index)

## [4.1.5]: 2022-01-10

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

[Terug naar het overzicht](#_index)

## [1.0.0] 2021-12-23  

- De Tabel module is beschikbaar op Productie. Met deze module kan je een tabel toevoegen aan de content. Merk op dat dit een losstaande content component is en niet een onderdeel van een Tekstvak met Opmaak. Je bepaalt zelf de rijen en kolommen en geeft op wat je in elke cell wil plaatsen zoals bv een tekstvak, een telefoonnummer, etc.


[Terug naar het overzicht](#_index)

## [4.1.2]: 2021-12-14 

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

## Vragen?
De releases worden op basis van een lange termijn en korte termijn planning samengesteld op basis van de behoefte van de afnemers van het platform. Staat er iets niet tussen of heb je een vraag over de release notes? contacteer dan erik.lenaerts@digipolis.be
