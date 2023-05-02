# Create Content Item
## POST Content
Gebruik de `POST` operatie via het [ACPaaS WCM Content Manager endpoint](/wcmv4/content/endpoint-content-manager) zoals hieronder staat afgebeeld.

```shell
POST '/acpaas/wcm-content-manager/v4/proxy/admin/content/v1/sites/{id}/content' \
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```


> [!INFO|label:Info]
> **Hoe herkent de WCM deze applicatie?**
> 
> Bij elke API call geef je een `api-key` mee. De API Gateway (Kong) verrijkt met een `JWT up-token`. In dit token zal de application identifier zitten, i.e. `moniker`. Deze identifier heeft dan toegang gekregen via het inrichten van de WCM credentials.

## Haal een sample Payload op
Het gemakkelijkste is dat je eerst in de redactie manueel een content item aanmaakt. Dit content item vraag je vervolgens op via de API en zo bekom je een sample payload die je kan gebruiken in je POST operatie. Het opvragen van deze sample, doe je ook via de WCM Content Manager API.

```shell
GET '/acpaas/wcm-content-manager/v4/proxy/admin/content/v1/sites/{id}/content/{content-uuid}
```

> Om content te schrijven heb je het interne id nodig van het content type. Dit content type id kan je enkel ophalen via de WCM Content Manager API. *(Er is een story op de backlog waarmee je straks ook content kunt aanmaken door de naam te geven van het content type ipv de interne id.)*


Die output ziet er in grote lijnen als volgt uit: 

```json
{
   "_id": "61f810490fff360009cb04eb",
   "fields": {
      ...
   },
   "meta": {
      ...
   },
   "uuid": "12010bd4-d7bb-4d2f-9dcf-4f152e9099a5"
}
```

> *Vermits we content gaan maken, mag je de `_id` en `uuid` al laten vallen, die zal het systeem voor ons aanmaken.*

Uit de sample kan je alles overnemen van het `fields` element:

```json
{
   "fields": {
       "teaser": "Lorum Ipsum",
       "titel": {
           "text": "Hello World",
           "textType": "h1"
       }
       ...
       "bijlagen": [],
       "paragrafen": [
           {
               "multiple": false,
               "componentType": null,
               "componentName": "tekst",
               "semanticType": "tekst",
               ...
               "value": "<b>Hello</b> World"
           }
       ],
   },
   "meta": {
      ...
   }
}
```

De volgorde van de json elementen uit het `fields` luik is niet belangrijk.

Voor het `meta` gedeelte heb je minstens volgende zaken nodig: 

```json
{
   "fields": {
       ...
  },
   "meta": {
        "label": "Hello World",
        "site": "85c0b6d0-a800-4bc8-8215-a92869dded22",
        "contentType": "60a60bba74572400097fc06c",
        "status": "PUBLISHED",
        "workflowState": "gepubliceerd",
        "published": true,
        "lang": "nl",
        "slug": {
            "nl": "hello-world",
            "multiLanguage": true
        },
        "urlPath": {
            "nl": {
                "pattern": "/nieuws/[item:slug]",
                "value": "/nieuws/hello-world"
            }
        },
        "activeLanguages": [ "nl" ]
   },
}
```

> [!WARNING|label:Belangrijk]
> * Het `label` vul je in met …?
> * De `site id` is belangrijk om aan te geven voor welke site je dit content item aanmaakt
> * Het `contentType` is op basis van de interne id die je bekomt via het ophalen van een sample hierboven
> * De status is één van: `DRAFT`, `PUBLISHED`, `UNPUBLISHED`
> * De `workflowState` moet eveneens de status volgen, met keuze uit: `werkversie`, `gepubliceerd`, `gearchiveerd` 
> * `published` zet je bij de create enkel op `true` als je de status `PUBLISHED` gebruikt. In alle andere gevallen geef je `false` mee.
> De `slug` is een object met de taalaanduiding
> Het `urlPath` is niet nodig wanneer je een [content blok](/common/content/concept-cb) aanmaakt.