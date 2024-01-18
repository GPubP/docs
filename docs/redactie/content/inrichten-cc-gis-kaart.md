# GIS kaart

Laat toe om een GEO kaart te kiezen en hierop elementen te tekenen.

> Zorg ervoor de de [GIS module](/modules/content/modules/module-gis) geactiveerd is.

## Voor content beheerders

Je kan 3 zaken configureren wanneer je een GIS kaart content component op je content type zet:

- GIS basiskaarten
- Element kleuren
- Extra velden per element

### GIS basiskaarten

De GIS basiskaarten bepaalt wat de redacteur ziet wanneer hij/zij de GIS kaart content component bewerkt.

Standaard is volgende basiskaart voorzien die de Vlaanderen in beeld brengt en specifiek Antwerpen daarboven in kleur zet:

[Vlaanderen als grijze achtergrond en Antwerpen in kleur](https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x})

```shell
https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x}
```  

Wil je de hele wereld in een grijze achtergrond dan kan je deze basiskaart configureren:
  
[De wereld als grijze achtergrond](https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x})

```shell
https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x}
```  

> [!info|label:Opmerking]
> Je kan verschillende basiskaarten als lagen op elkaar leggen. Wil je bijvoorbeeld zowel de wereld in't grijs en Antwerpen gekleurd daarboven dan gebruik je beide basiskaarten.

### Element kleuren

Als content beheerder kan je verschillende kleuren configureren. De redacteur kan per element dat hij/zij tekent de kleur kiezen.

Standaard hebben we volgende kleuren voorzien.

| Naam                        | HEX    |
|-----------------------------|--------|
| Afval en recyclage (petrol) | 007FA3 |
| Mobiliteit (grijs)          | 506D85 |
| Gezondheid (blauw)          | 0057B7 |
| Sporten en bewegen (groen)  | 007B5F |
| Kinderen en jeugd (paars)   | 8031A7 |
| Onderwijs (wijnrood)        | 840B55 |
| Cultuur (oranje)            | C05131 |
| Dienstverlening (stadsrood) | CF0039 |

### Extra velden per element

Als content beheerder kan je een [samengesteld content component](/common/content/concept-cc?id=standaard-samengesteld-en-custom) toevoegen aan een GIS kaart.
Dit component zal getoond worden aan de redacteurs waar ze de extra informatie kunnen invoeren per getekend element.

![Extra velden GIS kaart](../assets/gis-kaart-config.png "GIS kaart extra velden")

## Voor redacteurs

Als redacteur krijg je de optie om een GIS kaart toe te voegen.

![GIS kaart toevoegen](../assets/gis-kaart-1.png "GIS kaart toevoegen")

Je krijgt de GIS kaart editor en je de kaart zien die de content beheerder voor je heeft ingesteld. Standaard is het de kaart die Vlaanderen in't grijs toont en Antwerpen daarop gekleurd.

![Default GIS kaart](../assets/gis-kaart-2.png "Default GIS kaart").

Aan de rechterkant van de kaart bevinden zich de teken tools zoals een cirkel een polygoon, etc. Afhankelijk van wat de content beheerder heeft ingesteld kan je met één of meerdere kleuren tekenen.

![Teken elementen op de GIS kaart](../assets/gis-kaart-3.png "Teken elementen op de GIS kaart").

Per element dat je tekent kan je de naam aanpassen en extra informatie voorzien. Deze extra info is per getekend element hetzelfde maar kan per [content type](/common/content/concept-ct) verschillen.

![Extra info per element op de GIS kaart](../assets/gis-kaart-4.png "Extra info per element op de GIS kaart").

Je kan ook reeds eerder getekende elementen importeren, hiervoor moet de import wel voldoen aan het [GeoJSON](https://geojson.org/) standaard formaat.

![Elementen importeren op de GIS kaart](../assets/gis-kaart-6.png "Elementen importeren op de GIS kaart").

## Voor ontwikkelaars

### Lege output

```json
{
    "_id": "65a94d1c396a9a34304c2334",
    "uuid": "d2d8679a-3a5e-4ff6-a351-67becd6f5b7b",
    "fields": {
        "gis-kaart": ""
    },
    "modulesData": {}
}
```

### Output met een getekend element op de GIS kaart

Het content component in dit voorbeeld heeft de naam `gis-kaart`. Hierin zitten 2 luiken

`mapControls`: hier zitten gegevens die je nodig hebt voor de kaart zelf te renderen. De positie en de zoom dat de redacteur instelde toen hij/zij de GIS kaart afsloot worden hierin vastgelegd.
Zo kan de frontend kiezen om dit over te nemen bij de presentatie van de kaart

`mapData`: hier zit de GeoJSON data in met de getekende elementen.

?> [Bekijk hier](/frontend/content/geo-rendering?id=renderen-via-leaflet) hoe je best omgaat met het renderen van deze GIS kaart en de elementen erop.

```json
{
    "_id": "659d60edae970038264276cc",
    "uuid": "dac8e1ce-8b6c-437a-9191-c8981ba19a28",
    "fields": {
        "gis-kaart": {
            "mapControls": {
                "latLng": {
                    "lat": 51.23462231776156,
                    "lng": 4.424743652343751
                },
                "zoom": 13
            },
            "mapData": {
                "type": "FeatureCollection",
                "features": [
                    {
                        "type": "Feature",
                        "properties": {
                            "type": "polygon",
                            "color": {
                                "label": "Afval en recyclage (petrol)",
                                "value": "#007FA3"
                            },
                            "area": 5632544.62,
                            "perimeter": 10088.43,
                            "name": "Veelhoek 1",
                            "fields": {
                                "code": {
                                    "textType": "div",
                                    "text": "ABCDE"
                                },
                                "contact-e-mail": "erik.lenaerts@digipolis.be",
                                "contact-naam": {
                                    "textType": "div",
                                    "text": "Erik Lenaerts"
                                }
                            }
                        },
                        "geometry": {
                            "type": "Polygon",
                            "coordinates": [
                                [
                                    [
                                        4.431975,
                                        51.22828
                                    ],
                                    [
                                        4.431975,
                                        51.24322
                                    ],
                                    [
                                        4.480566,
                                        51.24322
                                    ],
                                    [
                                        4.480566,
                                        51.22828
                                    ],
                                    [
                                        4.431975,
                                        51.22828
                                    ]
                                ]
                            ]
                        },
                        "id": 213,
                        "style": {
                            "color": "#007FA3"
                        }
                    }
                ]
            }
        }
    },
    "modulesData": {}
}
```
