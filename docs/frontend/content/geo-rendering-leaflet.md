# Renderen via leaflet

## Render de kaart

!> TODO: beschrijf hoe je via leaflet GIS data kan tonen (zowel de kaart als de referentie)

Als je de kaart presenteert kan je gebruik maken van de `mapControls` informatie die je op het content item terug vindt.
Specifiek kan je de **positie** van de kaart zetten op basis van de `latlng` waardes uit het content item.
Daarnaast kan je de kaart **inzoomen** volgens de `zoom` waarde uit het content item.

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
            "mapData": { ... }
        }
    }
}
```

## Render de elementen op de kaart

!> TODO: beschrijf hoe je elementen rendert

!> TODO: beschrijf specifiek hoe je met circles moet omgaan op een kaart

