# Events

> [!info|label:Definitie]
> Sommige toepassingen willen zich abonneren op gebeurtenissen die zich voordien in de Redactie/WCM. Een typisch voorbeeld is de `content published` gebeurtenis. Vooraleer je hiermee aan de slag kan gaan, zal je deze gebeurtenis moeten ontsluiten naar de buitenwereld door deze af te leveren aan de [ACPaaS Event Handler](https://acpaas.digipolis.be/nl/product/event-handler-engine). Hieronder lees je hoe je dit configureert. 

Via het specifiek ontsluiten van interne gebeurtenissen beperken we het overvloedig vloeien van events naar buiten toe en kunnen we ook veilig te werk gaan. Is er een afnemer gecompromiteerd, dan kunnen we met één druk op de knop de stroom onderbreken. 

## Concepten

Een [tenant beheerder](/redactie/content/toegang-tenant-beheerder) kan [bestemmingen](/redactie/content/inrichten-events?id=bestemmingen) en [afleveringen](/redactie/content/inrichten-events?id=aflevering) configureren via de Redactie. Via een bestemming kan je aangeven welke namespace er gebruikt zal worden voor het afleveren van events. In een aflevering specifieer je welke [interne gebeurtenis](/redactie/content/inrichten-events?id=interne-gebeurtenissen) het systeem moet afleveren op welke bestemming. Hieronder zie je een schematisch overzicht van de basis concepten van de Event module.

![Event bestemmingen](.//redactie/assets/wcmv4-event-handler-module-simplified-4.png 'Configureer je bestemmingen (delivery channels) en je afleveringen (deliveries)')

## Interne gebeurtenissen

Er zijn heel veel interne gebeurtenissen die doorheen het systeem vloeien. Een aantal ervan kan je reeds naar buiten toe doorsluizen. Deze tabel geeft een overzicht van de huidige gebeurtenissen die je kan afleveren.

| Bron              | Gebeurtenis          | Omschrijving                                                                                 |
|-------------------|----------------------|----------------------------------------------------------------------------------------------|
| content           | created              | Wanneer een content item gemaakt is                                                          |
| content           | published            | Elke keer wanneer het content item gepubliceerd is.                                          |
| content           | archived             | Waneer het content item gearchiveerd is.                                                     |
| content           | draft_saved          | Waneer het content item als werkversie bewaard is. Dit is ook voor workflowState verandering |
| content           | publish_planned      | Waneer het content item gepland is om te publiceren.                                         |
| content           | removed              | Wanneer een content item verwijderd is                                                       |
| view              | created              | Wanneer een view gemaakt is                                                                  |
| view              | updated              | Wanneer een view aangepast is                                                                |
| view              | removed              | Wanneer een view verwijderd is                                                               |
| content-type      | created              | Wanneer een content type of blok gemaakt is                                                  |
| content-type      | updated              | Wanneer een content type of blok aangepast is                                                |
| content-type      | removed              | Wanneer een content type of blok verwijderd is                                               |
| content-component | created              | Wanneer een content component of blok gemaakt is                                             |
| content-component | updated              | Wanneer een content component of blok aangepast is                                           |
| content-component | removed              | Wanneer een content component of blok verwijderd is                                          |
| taxonomy          | rearranged           | Wanneer de termen van een taxonomie van plaats veranderen                                    |
| taxonomy          | term.created         | Wanneer een taxonomie term gecreëerd is                                                      |
| taxonomy          | term.updated         | Wanneer een taxonomie term aangepast is                                                      |
| taxonomy          | term.removed         | Wanneer een taxonomie term verwijderd is                                                     |
| search            | content.indexed      | Wanneer een content item geïndexeerd is                                                      |
| search            | index.content.upsert | Content item upsert index job in queue                                                       |
| search            | index.content.remove | Content item remove from index job in queue                                                  |

De volledige lijst van interne gebeurtenissen kan je hier bekijken: https://docs.google.com/spreadsheets/d/1pklN0Bgul3PFirLnTuMGsTPLnCc3cp7gXEia5y3-0oc/edit?usp=sharing. 

!> Zijn er interne gebeurtenissen die je nodig hebt voor je project, dan kunnen we ze op aanvraag ook ter beschikking stellen. Dit vergt extra maatwerk, niet onmogelijk maar het vraagt wel wat tijd. 

## Events configureren

De configuratie kan je vinden op [tenant](/common/content/concept-tenant) niveau op voorwaarde dat je de [Event module](/modules/content/modules/module-events) hebt geactiveerd voor je tenant.

![Events configureren](.//redactie/assets/events-configuratie-1.jpg 'Configureer je events')


### Bestemmingen
Het eerste wat je zal configureren is een bestemming op de Event Handler. In essentie stel je hier de `namespace` en de `ownerkey` in. Je kan deze bestemming hergebruiken voor verschillende [afleveringen](/redactie/content/inrichten-events?id=aflevering). 

> **Namespace** en **Ownerkey** zijn concepten uit de ([ACPaaS Event Handler Engine](https://acpaas.digipolis.be/nl/product/event-handler-engine/v2.0.0/features)). 

### Aflevering
Hier configureer welke [interne gebeurtenis](/redactie/content/inrichten-events?id=interne-gebeurtenissen) je wil doorsluizen naar de Event Handler Engine. 

Je kan een aflevering (delivery) als volgt opzetten:

1. kies het event
2. kies je bestemming
3. selecteer je topic (*) voor de gekozen bestemming
4. optioneel stel je nog een extra filter in.
5. test je event aflevering
6. activeer het afleveren. (Dit is vooral handig om tijdelijk de stroom de pauzeren)

> (*) **Topic** is een concept uit de Event Handler Engine

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
    operator: '<operator>',
    path: '<path>',
    value: '<value>'
}
```
Er kunnen meerdere filters gecombineerd worden. De combinatie van alle filters gaat dmv een logische AND operatie. Je kan naast `AND` ook gebruik maken van `OR`.

```json
{
  operator: 'AND',
  conditions: [
    {
      operator: '<operator>',
      path: '<path>',
      value: '<value>'
    }
  ]
}
```

#### Voorbeelden

**Filter op site**
```json
{
    operator: '=',
    path: '$.data.site.name',
    value: 'politieantwerpen.be'
}
```

**Filter op meerdere content types**
```json
{
  operator: 'OR',
  conditions: [
    {
      operator: '=',
      path: '$.data.contentType.name',
      value: 'crisis-bericht'
    },
    {
      operator: '=',
      path: '$.data.contentType.name',
      value: 'nieuws-bericht'
    }
  ]
}
```

**Filter op site en content type**
```json
{
  operator: 'AND',
  conditions: [
    {
      operator: '=',
      path: '$.data.contentType.name',
      value: 'crisis-bericht'
    },
    {
      operator: '=',
      path: '$.data.site.name',
      value: 'politieantwerpen.be'
    }
  ]
}
```

**Filter op site en twee verschillende content types**
```json
{
  operator: 'AND',
  conditions: [
    {
      operator: '=',
      path: '$.data.site.name',
      value: 'politieantwerpen.be'
    },
    {
      operator: 'OR',
      conditions: [
        {
          operator: '=',
          path: '$.data.contentType.name',
          value: 'crisis-bericht'
        },
        {
          operator: '=',
          path: '$.data.contentType.name',
          value: 'nieuws-bericht'
        }
      ]
    }
  ]
}
```

> [!tip|label: Tip]
> Om te kijken waarop je allemaal kan filteren ga je naar het **test scherm van je aflevering**. Daar staat een voorbeeld event payload dat je als lijdraad kan hanteren voor het opbouwen van je paden.

> [!tip|label: Tip]
> Je kan gebruik maken van https://webhook.site om je event data te zien aan de andere kant. Hiervoor moet je deze webhook url wel als subscriber inrichten in de event handler.


## Hou je content cache up to date
Configureer volgende events waarop je kan luisteren om je eigen content cache up te date te houden: 

Maak 2 `topics` aan in de Event Handler
- Content.Published
- Content.Removed


Configureer 3 `afleveringen` aan in de Redactie
- <prefix>.Content.Published naar topic Content.Published
- <prefix>.Content.Archived naar topic Content.Removed
- <prefix>.Content.Removed naar topic Content.Removed

Voorzie al dan niet extra filters zoals bijvoorbeeld een site filter. 

Het is een best practice om de aflevering een prefix te geven op basis van de afnemer. Zo kan je sneller jouw afleveringen vinden tussen de lijst.

Merk op dat het Content.Published event elke keer wordt afgevuurd bij een publicatie. Of het nu gaat over een nieuw content item dat gepubliceerd wordt of reeds een bestaand dat geherpubliceerd wordt. 

Zoals je merkt worden zowel de `Removed` als `Archived` events naar hetzelfde topic gestuurd in de Event Handler met deze configuratie. Voor een cache is dit hetzelfde, het content item mag niet meer voorkomen in je toepassing.



> [!Warning]
> Op het moment van schrijven is er nog geen `view.content.changed` event. Hierdoor is het nog niet mogelijk om te ontdekken dat content van een view veranderd is. 

## Events consumeren

Als afnemer van het GPubP kan je luisteren (subscriben) naar de geconfigureerde events. [Lees hier](/frontend/content/events-consumeren) hoe je ermee aan de slag gaat.
