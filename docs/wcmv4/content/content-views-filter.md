# Content via een view filteren 

## Vaste filters
Het gebeurt vaak dat je een view inricht in de redactie waar je bepaalde voorwaarde hebt aan gekoppeld. Hieronder is een schermvoorbeeld waarbij een view resulteert in een lijst van snelheidscontroles die tussen 2 data vallen.

![View](../assets/gpubp-view.jpg 'Configuratie van een view')

Elke keer dat de data van deze view wordt opgevraagd via een API call, zal dit in gefilterde data resulteren volgens de geconfigureerde filter instellingen.

*Haal gefilterede content op via een view*
```shell
GET .../view?uuid=42bb5422-74a4-4ed9-aba9-f01a8ee5040c 
```

## Dynamische filters
Vaak zijn de filter criteria niet vast. Het is de context die de waardes gaat bepalen en deze wordt bepaald door de afnemer van de view data (meestal de frontend). 

We moeten dus de waardes kunnen meegeven met de API call. Dit noemen we ook wel eens ‘dynamische views’.

### Filter syntax

In de WCMv4 zijn we verder gegaan en is het mogelijk om meteen in de API calls je  voorwaarden te definiëren. Hiervoor is er een syntax uitgewerkt op basis van operatoren.

*Haal all content items op volgens de laatste-nieuws view sinds 10 oktober 2021 vanaf 12h.*
```shell
GET .../view?uuid=42bb5422-74a4-4ed9-aba9-f01a8ee5040c&page=1&pagesize=20&fields.startdate.$gte=2021-10-10T12:00:00.000Z&lang=nl 
```

Naast `$gte` (gelijk of groter dan) zijn er nog andere operatoren die je kan gebruiken. Hier is een overzicht van de operatoren die je kan gebruiken bij views afhankelijk van het datatype van het veld.

| **operator description**                                            | **operator** | **string** | **number** | **date** | **datetime** | **boolean** | **array** | **taxonomy** | **field** |
|---------------------------------------------------------------------|--------------|------------|------------|----------|--------------|-------------|-----------|--------------|-----------|
| Matches values that are (exact) equal to a specified value.         | **$eq**      | Yes        | Yes        | Yes      | Yes          | Yes         | Yes       | Yes          |           |
| Matches values that are greater than a specified value.             | **$gt**      | Yes        | Yes        | Yes      | Yes          |             | Yes       |              |           |
| Matches values that are greater than or equal to a specified value. | **$gte**     | Yes        | Yes        | Yes      | Yes          |             | Yes       |              |           |
| Matches values that are less than a specified value.                | **$lt**      | Yes        | Yes        | Yes      | Yes          |             | Yes       |              |           |
| Matches values that are less than or equal to a specified value.    | **$lte**     | Yes        | Yes        | Yes      | Yes          |             | Yes       |              |           |
| Matches all values that are not equal to a specified value.         | **$not**     | Yes        | Yes        | Yes      | Yes          | Yes         | Yes       | Yes          |           |
| Matches any of the values specified in an array.                    | **$in**      | Yes        | Yes        | Yes      | Yes          |             | Yes       | Yes          |           |
| Matches none of the values specified in an array.                   | **$nin**     | Yes        | Yes        | Yes      | Yes          |             | Yes       | Yes          |           |
| Matches values that contain the specified value.                    | **$srch**    | Yes        |            |          |              |             | Yes       |              |           |
| Matches all of the values specified in an array.                    | **$all**     |            |            |          |              |             | Yes       | Yes          |           |
| size of the array equals the given value                            | **$size**    |            |            |          |              |             | Yes       |              |           |
| Matches items that have the specified field.                        | **$exists**  |            |            |          |              |             |           |              | Yes       |

### Filteren op een waarde

*Haal all content items op die een nis-landcode hebben kleiner dan 500*
```shell
GET .../view?uuid=2320fe31-28ff-4492-b6ee-0a227aaa800c&page=1&pagesize=20&fields.nis-landcode.$lt=500&lang=nl 
```

### Filteren op een dieperliggende waarde

*Haal all content items die een titel H1 opgemaakte titel hebben*
```shell
GET .../view?uuid=2320fe31-28ff-4492-b6ee-0a227aaa800c&page=1&pagesize=20&fields.titel.textype.$eq=h1&lang=nl 
```

### Filteren op een dieperliggende waarde

*Haal all content items die een getagged zijn met taxonomie term id 662 of 663*
```shell
GET .../view?uuid=2320fe31-28ff-4492-b6ee-0a227aaa800c&page=1&pagesize=20&fields.relatie-tot-antwerpen.$in=663,662&lang=nl 
```


### Filteren op de aanwezig van een veld
Dit is wellicht een speciale case, maar je kan de content items filteren in een view op voorwaarde dat een veld met een gegeven naam aanwezig is.

*Haal all content items op waar er een adres.label is. In die gevallen waar er via de adres component niets is gekozen, zal er ook geen label veld zijn voor het adres.*
```shell
GET .../view?uuid=42bb5422-74a4-4ed9-aba9-f01a8ee5040c&page=1&pagesize=20&adres.label.$exists=true&lang=nl
```