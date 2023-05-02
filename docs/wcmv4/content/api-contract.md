# API contract

In grote lijnen loopt het bekomen van een contract als volgt: 

1. [Definieer je app in het open platform](/wcmv4/content/api-contract?id=app-definiëren-in-het-open-platform)
2. zoek je API in de marketplace
3. vraag een contract aan
4. wacht op goedkeuring 
5. je bekomt een API key TODO: (identifier?)


## App definiëren in het open platform
Ga naar http://publisher.digipolis.be en registreer je afnemer die de API gaat afnemen. Dit levert je een `moniker` op.

### App config opzetten
Zet je een app op in app config (op ACC en/of PROD). Stel onder de Advanced Settings de identifier in als volgt:

* **Organisation ID:** `openplatform` *letterlijk overnemen*
* **Application ID:** `<moniker>`
* **Version ID:** `v1` *letterlijk overnemen* 

![API config](../assets/api-config.jpg 'API config')

!> Todo: beschrijf de overige stappen