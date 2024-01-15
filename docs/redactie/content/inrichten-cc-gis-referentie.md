# GIS referentie

Laat toe om een GIS punt te kiezen uit een lijst van GIS lagen. bv één specifiek apother uit de GIS apother laag van Antwerpen.

> Zorg ervoor de de [GIS module](/modules/content/modules/module-gis) geactiveerd is.

## Voor content beheerders
Er zijn geen configuratie opties voor de contentbeheerder.

## Voor redacteurs
Een redacteur kiest eerst een `GIS laag` zoals **Stadsloketten**. Vervolgens kiest hij of zij een punt uit die laag zoals het **Stadsloket Berchem**. 

![Gis Referentie](.//redactie/assets/gis-referentie.jpg 'Kies een laag en punt uit het GIS systeem.')


## Voor ontwikkelaars

De waarde van het component is op basis van de sleutel/key. Het label komt niet in de api payload mee.

## Lege output

```json
{
    "_id": "659d4ccef3a6b83cb48ac709",
    "uuid": "951a77cb-1df9-4978-a44e-d3ee0c8bca9f",
    "fields": {
        "gis-referentie": {
            "layerId": "empty",
            "gisId": ""
        }
    },
   ...
}
```

## Output met gekozen waarden

```json
{
    "_id": "659d4ccef3a6b83cb48ac709",
    "uuid": "951a77cb-1df9-4978-a44e-d3ee0c8bca9f",
    "fields": {
        "gis-referentie": {
            "layerId": "2",
            "gisId": "PUB307"
        }
    },
   ...
}
```


## Voor bezoekers
Dit is afhankelijk van hoe een [kaart gerenderd](/frontend/content/geo-rendering) wordt in de frontend. 
