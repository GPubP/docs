# Content opvragen via views
Om een **lijst** op te halen met meerdere content items, maak je gebruik van een view. Deze [configureer](/redactie/content/inrichten-views) je op voorhand in de redactie. Hieronder een screenshot van de redactie waar je de views maakt en kan beheren:

Een lijst ophalen kan je via hetzelfde [WCM Proxy endpoint](/wcmv4/content/endpoint-proxy) doen als waar je één content item ophaalt. Dit keer maak je gebruik van het `view` path. 

*Haal alle content items op volgens de `laatste-nieuws` view.*
```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/view?uuid={id-van-laatste-nieuws-view}&lang=nl
```

Merk op dat je niet alle content items gaat terugkrijgen, maar eerder een beperkte lijst. Dit volgt het [paging principe van het Antwerp API System](https://antwerp-api.digipolis.be/#/content/developers/paging). 

```json
{
   "_links": {
       "self": { "href": ".../sites/8fd9f2...e5890390/views?uuid42bb.." },
       "first": { "href": ".../sites/8fd9f2...e5890390/views?uuid42bb..&page=1&pagesize=10" },
       "last": { "href": ".../sites/8fd9f2...e5890390/views?uuid42bb..&page=2&pagesize=10" }
   },
   "_embedded": [
	...
   ],
   "_page": {
       "size": 10,
       "totalElements": 2,
       "totalPages": 1,
       "number": 1
   }
}
```


Je kan zelf de `page` en `pagesize` parameter toevoegen om zo de lijst groter of kleiner te maken.

*Haal alle content items op volgens de laatste-nieuws view met eigen paging instellingen.*
```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/view?uuid={id}&page=2&pagesize=20&lang=nl
```