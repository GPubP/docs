# Assets API

## Assets ophalen
Het ophalen van afbeeldingen of bestanden is vrij eenvoudig en je hebt hiervoor enkel een `id` nodig. Deze id kan je terugvinden wanneer je [content ophaalt](/wcmv4/content/content-item-read) waarin een [afbeelding content component](/redactie/content/inrichten-cc-afbeelding) voorkomt.

*Via deze call haal je één specifieke asset op*
```shell
GET .../assets/v1/sites/[siteId]/assets/cb293e6c-e10a-4dda-a296-3fee2840d86e/file 
```

## Crops
Typisch kiest een redacteur een afbeelding en maakt hij/zij één of meerdere crops. Het aantal crops is vastgelegd op het content type. Voor elke crop gaat de WCM een extra afbeelding bewaren. Met andere woorden, elke crop is een individuele asset op zich. Zijn er op een afbeelding van een content type, 4 crops, dan zal het systeem 5 afbeeldingen bewaren, nl. 1 voor de originele en 4 extra afbeeldingen voor elke crop. 

Hieronder zie je een voorbeeld payload bij het ophalen van een content item met 2 crops `small` en `medium`. 


```json
{
   "_id": "60e5abd49cc9940009fbf124",
   "fields": {
       "afbeelding": {
           "afbeelding": {
               "meta": {
                   "name": "Mijn afbeelding",
                   "alt": "Mijn afbeelding",
                   "title": "Mijn afbeelding",
                   "description": "omschrijving",
                   "copyright": "",
                   "figuratively": true
               },
               "original": {
                   "asset": {
                       "mime": "image/jpeg",
                       "uuid": "4ed0c27a-1b38-4718-9bce-7f0dadda48c5",
                       "size": {
                           "height": 1305,
                           "width": 2320
                       },
                       "fileName": "IMG_20210925_155306-2.jpg"
                   }
               },
               "crops": {
                   "small": {
                       "asset": {
                           "fileName": "IMG_20210925_155306-2.jpg",
                           "mime": "image/jpeg",
                           "size": {
                               "width": 1740,
                               "height": 1305
                           },
                           "uuid": "774522b9-31e2-4c05-b17f-faa183218963"
                       },
                       "cropValues": {
                           "x": 290,
                           "y": 0,
                           "width": 1740,
                           "height": 1305
                       },
                       "transformValues": {
                           "grayscale": false,
                           "blur": 0,
                           "rotate": 0
                       }
                   },
                   "medium": {
                       "asset": {
                           "fileName": "IMG_20210925_155306-2.jpg",
                           "mime": "image/jpeg",
                           "size": {
                               "width": 2320,
                               "height": 1160
                           },
                           "uuid": "c03ac0fb-d9cd-4678-9f60-a1d72ed70903"
                       },
                       "cropValues": {
                           "x": 0,
                           "y": 73,
                           "width": 2320,
                           "height": 1160
                       },
                       "transformValues": {
                           "grayscale": false,
                           "blur": 0,
                           "rotate": 0
                       }
                   }
               }
           }
       }
   },
   "meta": {
      ...
   },
   ...
}
```

Wil je de originele afbeelding ophalen? gebruik dan de `afbeelding.original.asset.uuid`. Wil je de afbeelding volgens de ‘small’ crop ophalen, gebruik dan de `afbeelding.crops.small.asset.uuid`. 

> `afbeelding` in dit voorbeeld is de naam van het afbeelding content component op het content type.

## Assets in een Tekstvak met Opmaak

Assets in tekstvak met opmaak zien er als volgt uit:

```html
<img source-url="/v1/proxy/admin/assets/v1/assets/b2465-...3876f/file?x-tenant-id=be54c7-...eee54" data-file-uuid="b2465-...3876f" src="/v1/proxy/admin/assets/v1/assets/b2465-...3876f/file?x-tenant-id=be54c7-...eee54">
```

Dit betekent dat er in de BFF een proxy moet voorzien worden dat dit pad omvormt naar het standaard default endpoint om assets aan te spreken:

*Pad in tekstvak met opmaak:*
```json
"/v1/proxy/admin/assets/v1/assets/[assetId]/file?x-tenant-id=[tenantId]"
```

*API call:*
```shell
GET .../assets/v1/sites/[siteId]/assets/[assetId]/file 
```







