# Een conten item opvragen

Via het [WCM Proxy endpoint](/wcmv4/content/endpoint-proxy) kan je één content item opvragen via z’n slug:

```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/content?slug={slug}&lang={lang}
```

De slug vind je terug in de redactie tool.

?> Merk op dat de **lang** parameter verplicht is (heeft meestal de waarde `nl` voor nederlands)

Het resultaat van deze **GET** operatie is een JSON document (aka de result payload) met volgende structuur:

```json
{
  "_id": "60b9ec5811264300093a98e2", 
  "uuid": "0d37b868-5e76-405f-9f2c-faf3f2e4de13",
  "fields": {
    ...
  },
  "meta": {
    ...
  },
  "references": {
    ...
  }
}
```

## Content

Wanneer je in de redactie een nieuw content type maakt, zal er hier standaard een `titel` en `teaser` in zitten naast SEO metadata velden.
Een content beheerder kan extra content componenten toevoegen zoals bv een adres. 
De content van een content item - gebaseerd op de geconfigureerd content componenten - vind je terug onder `fields` in de result payload.

```json
{
  "_id": "60b9ec5811264300093a98e2", 
  "uuid": "0d37b868-5e76-405f-9f2c-faf3f2e4de13",
  "fields": {
    "titel": "Kantoor Noorderlaan",
    "teaser": "Je kan langskomen op dit kantoor voor...",
    "adres": {
       "position": {
          "lng": 4.397878,
          "lat": 51.220153
        },
        "label": "kleine pieter potstraat (antwerpen)"
    },
    ...
  },
  "meta": {
    ... 
  },
}
```

## Metadata

Onder meta vind je metadata terug van het content item. Dit is informatie dat de WCMv4 bijhoud en nodig heeft om te kunnen werken, waaronder de slug, het `contenttype` waar dit item van gemaakt is, etc.

```json
{
  "_id": "60b9ec5811264300093a98e2", 
  "uuid": "0d37b868-5e76-405f-9f2c-faf3f2e4de13",
  "fields": {
    ...
  },
  "meta": {
    "slug": {
       "nl": "kantoor-noorderlaan"
    },
    "label": "Kantoor Noorderlaan",
    "contenttype": "kantoor",
    ... 
  },
}
```

## References

!> TODO: nog uitwerken.

?> Wil je draft content ophalen, oftewel content dat niet online staat, gebruik dan de WCM Content Manager [API history call](/wcmv4/content/content-history).
