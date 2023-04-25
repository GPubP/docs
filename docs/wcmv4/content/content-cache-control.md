# Cache control

De WCMv4 heeft standaard (server side) caching ingebouwd. Hiermee kunnen we complexere vraagstelling sneller leveren aan de afnemers. High level ziet het er als volgt uit: 

![WCMv4 cache](../assets/WCMv4-caching.png 'Een ingebouwde cache in de WCMv4 API')

In volgend sequence diagram zie je hoe dit by default werkt: 

![WCMv4 cache](../assets/WCMv4-caching-1.png 'Standaard gedrag van de WCMv4 API cache')

## Request HTTP headers
Met de `Cache-Control` header kan je als consumer aangeven om niet de gecachte versie terug te geven maar de actuele data. Dit kan in sommige gevallen even duren omdat het systeem intern het content item nog moet samenstellen.

```shell
GET {baseUrl}/wcm-proxy/v4/content/v1/sites/{siteId}/content?slug=xyz&lang=nl
--header 'Cache-Control: no-cache'
```

![WCMv4 cache](../assets/WCMv4-caching-2.png 'De WCMv4 API cache niet gebruiken')

## Response HTTP headers
Volgende cache headers worden teruggestuurd in een Response:

| Header              | Values        | Omschrijving                                                                                                                                                                                                                                                                                                                                                       |
|---------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| x-cache             | HIT \| MISS   | Hit: Het content item komt uit de WCM cache Miss: Het content item wordt opnieuw. samengesteld uit de onderliggende WCM storage.                                                                                                                                                                                                                                   |
| x-cache-invalidated | true \| false | Geeft aan dat deze versie die uit de cache komt niet up to date is. Dit kan zich voordoen wanneer er net een aanpassing is gedaan door een redacteur en dat deze wijziging nog niet gereflecteerd is in de WCM cache. true: het content item dat je van de WCM cache krijgt is (mogelijks) niet actueel. false: je hebt het meest recente en actuele content item. |
| x-cache-created     | ISODatetime   | Geeft aan wanneer deze cache entry gecreëerd is in de WCM cache.                                                                                                                                                                                                                                                                                                   |

Ingeval er net een aanpassing aan het content item is gebeurd, dan kan het heel even duren vooraleer de server cache opnieuw is opgebouwd. Zolang dit verversen bezig is, zal je dus een voorgaande gecachte versie terug krijgen met de `x-cache-invalidated=true` HTTP response header. Van zodra deze header false is, heb je een nieuwe versie.

![WCMv4 cache](../assets/WCMv4-caching-4.png 'De WCMv4 API cache latency')
