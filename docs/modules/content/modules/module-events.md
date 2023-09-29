# Events module

> [!info|label:Definitie]
> Met deze module kan je interne gebeurtenissen aka `events` afleveren aan de [ACPaaS Event Handler](https://acpaas.digipolis.be/nl/product/event-handler-engine). 

De WCMv4 bestaat uit vele modules die onderling uitvoerig informatie uitwisselen over een interne ruggegraat (Kafka). Dikwijls is de buitenwereld enkel geïnteresseerd in heel specifieke zaken en is het niet de bedoeling om alles naar buiten toe te brengen. Bijkomend is er een architecturale keuze gemaakt vanuit beveiligingsredenen om afnemers geen aansluiting te geven rechtstreeks op de interen kafka van de WCM.

![Event module concept](.//modules/assets/wcmv4-event-handler-module-simplified.png 'De event module die zorgt voor het afleveren van zeer specifieke events naar de buitenwereld')

Enkele use cases: 

* Een courant voorbeeld is een afnemer die een content cache heeft aangelegd en die bij een redactionele aanpassing z’n cache heel precies wil bijwerken, enkel dat stuk dat net veranderd is. 
* Een ander voorbeeld is een reporting afnemer die beleidsinformatie wil actualiseren in de datawarehouse op basis van content bewegingen.
* Het bijwerken van een taxonomie in een gekoppeld pakket zoals Salesforce
* Actvititeiten synchroniseren naar Uit in Vlaanderen
* ...

## Bron

Een bron is daar waar de gebeurtenis zich voordoet, zeg maar de plaats waar het interne event ontstaat. We denken hierbij vooral aan:
* veranderingen aan content zoals 
  * content items, taxonomieën, menu’s, sitestructuur, etc.
* veranderingen aan structuur
  * content types, blokken, componenten, views, workflows, rollen, rechten, etc
* module gebeurtenissen
  * generieke zoals: installed, enabled, disabled, removed, 
  * specifieke die expliciet exposed worden door de modules zoals de WCM Search module die aangeeft wanneer een content item geïndexeerd is.
* systeem gebeurtenissen
  * start, stop

![Event module concept](.//modules/assets/wcmv4-event-handler-module-simplified-2.png 'De event module met event bronnen')


## Interne events
Elke bron heeft een eigen lijst van gebeurtenissen aka ‘internal events’. De ‘Content’ bron heeft bv de volgende interne events:

* `created`
* `changed`
* `deleted`
* `status_changed`

## Register
De WCM bevat een intern Event Register. Dit is het telefoonboek van welke events er allemaal aanwezig zijn. Het register bevat informatie over de events, nl:

* de naam
* het type en bron, bv: 
  * `be.digipolis.wcm.v4.content.item.created`
  * `be.digipolis.wcm.v4.search.indexed`
* het json schema dat de data beschrijft van de gebeurtenis.

Het register speelt een cruciale rol in het Event mechanisme. Zonder dit kan de content beheerder niet kiezen uit een lijst van events om door te sluisen via de Event module. Het vormt ook de basis voor het genereren van de documentatie over de events. 


!> Todo: zet hier een link naar de AsyncAPI docs van het register. Voorlopig kunnen we verwijzen naar: https://docs.google.com/spreadsheets/d/1pklN0Bgul3PFirLnTuMGsTPLnCc3cp7gXEia5y3-0oc/edit#gid=0


### Eigen events registreren en uitsturen
Het is mogelijk om custom, eigengemaakte events te voorzien zodat specifieke scenario’s gesignaleerd kunnen worden waarop de Event module kan reageren. Dit kan door middel van een WCM BSL module te maken. Deze kan luisteren op interne kafka, doet er iets mee en zet op kafka z’n eigen signaal. Deze module zal zoals alle andere modules de custom event registreren in het algemene register. 

In de [Greetings developer gids - Hoofdstuk 6 werken met Events](/modules/content/developer-guides/greetings/step-6-events) kan je een voorbeeld hiervan zien.

## Events configureren

In de Redactie kan je de [events inrichten](/redactie/content/inrichten-events). 

## Events consumeren

Als afnemer van het GPubP kan je luisteren (subscriben) naar de geconfigureerde events. [Lees hier](/frontend/content/events-consumeren) hoe je ermee aan de slag gaat.


?> Ga terug naar het [overzicht van alle modules](/modules/content/wcm-modules)