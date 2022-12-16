# Adres
Kies een adres of een straatnaam.

Zie ook bij de component [Locatie](/redactie/content/inrichten-cc-locatie.md)

# Voor content beheerders
Vanaf 4.2 kan je een zoekbereik configureren. Hiermee kan je aangeven wat het adres component allemaal herkent. Zo kan je bv uitsluitend deze content component laten zoeken naar pleinen of districten.

![Adres configuratie](../assets/adres-config.jpg 'Configuratie opties van een Adres content component')

# Voor redacteurs
![Adres configuratie](../assets/adres-red.jpg 'Invoeren van een adres als redacteur')

# Voor ontwikkelaars
## Lege output
```json
{
   "_id": "60e5abd49cc9940009fbf124",
   "fields": {
       "adres": {}
   },
   "meta": {
      ...
   },
   ...
}
```

## Output voor een adres
Een adres is een straatnaam, huisnummer en postcode/district

```json
{
   "_id": "60e5abd49cc9940009fbf124",
   "fields": {
        "adres": {
            "formattedAddress": "Kerkstraat 2, 2060 Antwerpen",
            "crabAddressType": "hoofdadres",
            "addressPosition": {
                "geometryMethod": "AfgeleidVanObject",
                "lambert72": {
                    "x": 154201.6,
                    "y": 211960.5
                },
                "wgs84": {
                    "lat": 51.21757827,
                    "lng": 4.42889271
                }
            },
            "houseNumber": {
                "houseNumber": "2",
                "busNumber": ""
            },
            "street": {
                "streetNameId": 1514,
                "streetName": "Kerkstraat",
                "homonymAddition": ""
            },
            "municipalityPost": {
                "nisCode": 11002,
                "municipality": "Antwerpen",
                "antwerpDistrict": "Antwerpen",
                "antwerpDistrictCode": "AN",
                "postCode": "2060"
            },
            "crabAddressId": 1033182,
            "addressRegId": 1177958,
            "id": 136588,
            "layer": "adres",
            "label": "Kerkstraat 2, 2060 Antwerpen"
        }
   },
   "meta": {
      ...
   },
   ...
}
```


## Output voor een straatnaam
Een adres is een straatnaam en postcode/district

```json
{
   "_id": "60e5abd49cc9940009fbf124",
   "fields": {
        "adres": {
            "position": {
                "lambert72": {
                    "x": 154769.3,
                    "y": 210084.7
                },
                "wgs84": {
                    "lat": 51.200695,
                    "lng": 4.437005
                },
                "geometryShape": "Polygon",
                "geometry": null
            },
            "label": "borsbeeksebrug (berchem)",
            "antwerpDistrict": "Berchem",
            "postCodes": [
                "2600"
            ],
            "streetNameId": "408",
            "layer": "straatnaam",
            "streetName": "Borsbeeksebrug",
            "name": "Borsbeeksebrug",
            "fullId": "P_DA/Locaties/MapServer/18/1885568",
            "id": "1885568"
        }
   },
   "meta": {
      ...
   },
   ...
}
```

# Implementatie tips

* Gebruik een leaflet component in de frontend
* gebruik de volgende API om een adres obv een tekst om te zetten naar een object dat de wcm nodig heeft: 

```bash
curl --location --request GET 'https://locationpicker-app1-a.antwerpen.be/api/v2/addresses?streetname=Borsbeeksebrug&housenumber=38' \
--header 'apikey: {{apikey}}' \
```

?> Ga terug naar het [overzicht van alle content componenten](/redactie/content/inrichten-cc-standaard.md)