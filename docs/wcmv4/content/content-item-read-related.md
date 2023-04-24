# Gerelateerde content
Wanneer je content ophaalt, is dit enkel de data van dat item met de gegeven slug. Een content item kan op zich weliswaar verwijzen naar andere content door:
1. het kan één of meerdere content referenties bevatten naar andere content items
2. het kan een view referentie bevatten dat op zich resulteert in een lijst van content items

Gerelateerde content kan je ophalen door bijkomende API calls uit te voeren. Dit kan soms tot heel veel bijkomend API calls & netwerk trafiek leiden, wat voor performantie nadelig is. 

## Content referenties ophalen
> Gerelateerde content mee opvragen in één call, samen met het hoofd content item kan via de optionele populate parameter.

De `populate` (query) parameter zet je na de andere parameters zoals `slug` en `lang`.
```shell
GET /v1/sites/{siteId}/content?slug={slug}&lang={lang}&populate=... 
```

de populate query parameter werkt als volgt: Je geeft de naam op van het content referentie veld waarvan je de content wil toevoegen aan het resultaat. Enkele voorbeelden: 

*Haal content item regio-noord op, inclusief de content van het gelinkte kantoor.*
```shell
GET .../content?slug=regio-noord&lang=nl&populate=kantoor 
```

*Haal het product frisbee-rood op, inclusief de content van de gelinkte reviews. In dit voorbeeld heeft het product een content referentie onder de naam reviews dat ingesteld is op multiple. De redacteur kan dus meerdere reviews kiezen voor dit product.*
```shell
GET .../content?slug=frisbee-rood&lang=nl&populate=reviews 
```

*Haal het homepage content item home op, inclusief de content dat resulteert uit de gelinkte belangrijk-nieuws view.*
```shell
GET .../content?slug=home&lang=nl&populate=belangrijk-nieuws 
```

Uit deze voorbeelden zie je dat je enkel de naam van het veld (content component) moet meegeven wat je wil populeren. Als je een naam opgeeft van een veld dat op zich geen content referentie is, dan gebeurt er niets. Geef je een naam op van een veld dat niet bestaat krijg je eveneens een HTTP 200 terug.

## Meerdere content referenties tegelijk ophalen
Als je van een content item, meteen 2 of meerdere gerelateerde content wil ophalen, kan je dit in de populate parameter scheiden door een komma. 

*Stel je hebt een `factuur`, waarvan je de `factuurlijnen` en de `klant` wil ophalen in één call.*
```shell
GET .../content?slug=INV0012&lang=nl&populate=invoicelines,customer
```

> Geen spaties gebruiken voor of na de komma. (zie ook [RFC1738](https://www.rfc-editor.org/rfc/rfc1738)) 

## Dieper liggende content 
Er zijn situaties waarbij je content model bestaat uit meerdere niveaus. Zo heb je bijvoorbeeld een `homepage` met een `projecten` view referentie en elk project wordt door een `team` uitgevoerd. ~~Als je een 2e niveau wil ophalen, kan je dit doen door gebruik te maken van een punt.~~

!> Momenteel laat de API niet toe om dieper liggende gerefereerde content op te halen. 

```shell
GET .../content?slug=home&lang=nl&populate=projecten,projecten.team
-> HTTP 400 
```

*Haal de `homepage` op, met de content referenties (links) die vervat zit in een `toptaken` content component.*
```shell
GET .../content?slug=home&lang=nl&populate=toptaken-list.links
```
Geen spaties gebruiken voor of na het punt. (zie ook [RFC1738](https://www.rfc-editor.org/rfc/rfc1738)) 

## Recurring content referenties
Stel je hebt een content model waarbij je verwijst naar een content item van hetzelfde content type. Bijvoorbeeld een `Persoon` content type heeft een content referentie `vriend-van` van het type Persoon.  Net zoals bij [dieper liggende content](/wcmv4/content/content-item-read-related?id=dieper-liggende-content) ondersteunt de API geen recurring content referenties, ttz, je kan het eerste niveau ophalen, de API gaat niet verder dan dat.

*Haal content item Jefke op, inclusief z’n vriend (Jos). De vrienden van Jos worden niet opgehaald.*  
```shell
GET .../content?slug=jefke&lang=nl&populate=vriend-van 
```
## Alle content populeren
Wil je meteen alle content van het content item in één instructie populeren, gebruik je `populate=true`. 

*Stel je hebt een `factuur`, waarvan je de `factuurlijnen`, `klant`, `producten`, etc. wil ophalen.*
```shell
GET .../content?slug=INV0012&lang=nl&populate=true
```

## Content referenties voor fieldgroup en multiple

!> TODO: nog verder uitwerken. Merk op dat je nog wel gebruik kan maken van de dot-notatie wanneer content referenties in een fieldgroup of een multiple vervat zit. Idee is dat je niet de json afgaat voor de opbouw van de expressie (in tegenstelling tot filtering), zie ook https://jira.antwerpen.be/browse/RED-1502 