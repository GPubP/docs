# Content via een view filteren 
Het gebeurt vaak dat je een view inricht in de redactie waar je bepaalde voorwaarde hebt aan gekoppeld. Hieronder is een schermvoorbeeld waarbij een view resulteert in een lijst van snelheidscontroles die tussen 2 data vallen.

![View](../assets/gpubp-view.jpg 'Configuratie van een view')

De waardes van deze voorwaarden (de start - en einddatum in dit voorbeeld) zijn niet vast, deze zullen variëren. Het is de context die de waardes gaat bepalen en de context, deze wordt bepaald door de afnemer. Concreet wil dit zeggen dat de afnemer de waarde van de start - en einddatum gaat bepalen. We moeten dus de waardes kunnen meegeven met de API call. Dit noemen we ook wel eens ‘dynamische views’.

In de WCMv4 zijn we verder gegaan en is het mogelijk om meteen in de API calls je  voorwaarden te definiëren. Hiervoor is er een syntax uitgewerkt op basis van operatoren.

*Haal all content items op volgens de laatste-nieuws view sinds 10 oktober 2021 vanaf 12h.*
```shell
GET .../view?uuid=42bb5422-74a4-4ed9-aba9-f01a8ee5040c&page=1&pagesize=20&meta.lastModified.$gte=2021-10-10T12:00:00.000Z&lang=nl 
```

> Momenteel werkt het filteren op fields wel, maar nog niet op metadata. Bug [RED-1606](https://jira.antwerpen.be/browse/RED-1606) 


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

## Filteren op de aanwezig van een veld
Dit is wellicht een speciale case, maar je kan de content items filteren in een view op voorwaarde dat een veld met een gegeven naam aanwezig is.

*Haal all content items op waar er een adres.label is. In die gevallen waar er via de adres component niets is gekozen, zal er ook geen label veld zijn voor het adres.*
```shell
GET .../view?uuid=42bb5422-74a4-4ed9-aba9-f01a8ee5040c&page=1&pagesize=20&adres.label.$exists=true&lang=nl
```