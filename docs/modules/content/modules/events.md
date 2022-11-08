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


!> Todo: zet hier een link naar de AsyncAPI docs van het register. Voorlopig kunnen we verwijzen naar: https://docs.google.com/spreadsheets/d/1pklN0Bgul3PFirLnTuMGsTPLnCc3cp7gXEia5y3-0oc/edit#gid=0

### Je eigen interne events ?
Het is mogelijk om custom, eigengemaakte events te voorzien zodat specifieke scenario’s gesignaleerd kunnen worden waarop de Event module kan reageren. Dit kan door middel van een WCM BSL module te maken. Deze kan luisteren op interne kafka, doet er iets mee en zet op kafka z’n eigen signaal. Deze module zal zoals alle andere modules de custom event registreren in het algemene register. 

## Configuratie
Een [tenant beheerder](/redactie/content/toegang-tenant-beheerder) kan `bestemminngen` en `afleveringen` configureren via de Redactie. Via een bestemming kan je aangeven welke namespace er gebruikt zal worden voor het afleveren van events. In een aflevering specifieer je wat je gaat afleveren op die bestemming. Hieronder zie 

![Event bestemmingen](.//modules/assets/wcmv4-event-handler-module-simplified-4.png 'Configureer je afleveringen')

### Aflevering
Je kan een aflevering (delivery) als volgt opzetten:

1. kies het event
2. kies je bestemming
3. selecteer je topic voor de gekozen bestemming
4. optioneel stel je nog een extra filter in.

### Events verder filteren in een aflevering 

Niet alle interne events van een bepaald type moeten buiten gaan. Neem nu het `content.draft_changed` event, dat kan zijn dat de workflowstatus veranderd is naar `my-state` of naar `another-state` en je bent misschien enkel in deze laatste geïnteresseerd.
Of bijvoorbeeld het `created` event van de content module, je wil niet alle nieuwe content items, maar heel specifiek die van nieuwsberichten. 

Soms zijn er andere gebeurtenissen zoals een `changed` event van de taxonomie bron. Hier zal je een keuze van taxonomie boom moeten maken of misschien zelfs in uitzonderlijke gevallen slechts van een bepaalde tak van deze taxonomie boom. 

Door gebruik te maken van filters kan nauwer of breder te werk gaan. Zo kan je een filter maken voor alle gepubliceerde crisisberichten van de politieantwerpen.be site van deze tenant:

* `site.name == “politieantwerpen.be”`
* `contentType.name == “crisis-bericht”`

Vanwege de technische aard van deze module is er gekozen om voor de filters een bepaalde syntax te hanteren, i.e. json voor het geheel en https://jsonpath.com voor de paden.

Een filter bestaat uit een boolean expression dat resulteert in true of false. 

```json
{
  "operator": "AND",
  "conditions": [
    {
      "operator": "<operator>",
      "path": "<path>",
      "value": "<value>"
    }
  ]
}
```

Er kunnen meerdere filters gecombineerd worden. De combinatie van alle filters gaat dmv een logische AND operatie. De volle

#### Voorbeelden

**Filter op site**
```json
{
  "operator": "AND",
  "conditions": [
    {
      "operator": "=",
      "path": "$.data.site.name",
      "value": "politieantwerpen.be"
    }
  ]
}
```

**Filter op meerdere content types**
```json
{
  "operator": "OR",
  "conditions": [
    {
      "operator": "=",
      "path": "$.data.contentType.name",
      "value": "crisis-bericht"
    },
    {
      "operator": "=",
      "path": "$.data.contentType.name",
      "value": "nieuws-bericht"
    }
  ]
}
```

**Filter op site en content type**
```json
{
  "operator": "AND",
  "conditions": [
    {
      "operator": "=",
      "path": "$.data.contentType.name",
      "value": "crisis-bericht"
    },
    {
      "operator": "=",
      "path": "$.data.site.name",
      "value": "politieantwerpen.be"
    }
  ]
}
```

> [!tip|label: Tip]
> Om te kijken waarop je allemaal kan filteren ga je naar het **test scherm van je aflevering**. Daar staat een voorbeeld event payload dat je als lijdraad kan hanteren voor het opbouwen van je paden.

