# Taxonomy termen

## Read term
### Eén term 
```shell
GET '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/terms/{termid}'
```

In het pad geef je de `id` van de taxonomie.
In het pad geef je de `termid` van de term die je wenst op te vragen.

### Alle termen (de collectie)
```shell
GET /wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/terms'
```

In het pad geef je de `id` van de taxonomie waarvan je de termen wenst op te vragen.

Het resultaat van deze call is als volgt. De volgorde van de ‘siblings’ wordt aangegeven door middel van een `position` property. Later zullen we zien hoe we deze [in één keer kunnen ordenen](/wcmv4/content/taxonomy-terms?id=volgorde-veranderen).

```json
{
    "_embedded": [
        {
            "id": 40,
            "label": "Portefeuilles",
            "description": "",
            "taxonomyId": 5,
            "publishStatus": "published",
            "createdBy": "(unknown)",
            "createdAt": "2021-07-08T15:26:13.306057Z",
            "updatedBy": "(unknown)",
            "updatedAt": "2021-07-08T15:26:13.306057Z",
            "propertyValues": [
                {
                    "id": 15,
                    "key": "position",
                    "value": "0"
                }
            ],
            "parentTermId": 40
        },
        {
            "id": 42,
            "label": "Elektronica",
            "description": "",
            "taxonomyId": 5,
            "publishStatus": "published",
            "createdBy": "(unknown)",
            "createdAt": "2021-07-08T15:28:35.148407Z",
            "updatedBy": "(unknown)",
            "updatedAt": "2021-07-08T15:28:35.148407Z",
            "propertyValues": [
                {
                    "id": 11,
                    "key": "position",
                    "value": "1"
                }
            ],
            "parentTermId": 42
        },
        {
            "id": 44,
            "label": "Tablet",
            "description": "",
            "taxonomyId": 5,
            "publishStatus": "published",
            "createdBy": "(unknown)",
            "createdAt": "2021-07-08T15:29:11.081609Z",
            "updatedBy": "(unknown)",
            "updatedAt": "2021-07-08T15:29:11.081609Z",
            "propertyValues": [
                {
                    "id": 16,
                    "key": "position",
                    "value": "0"
                }
            ],
            "parentTermId": 42
        },
        {
            "id": 45,
            "label": "Fietsen",
            "description": "",
            "taxonomyId": 5,
            "publishStatus": "published",
            "createdBy": "(unknown)",
            "createdAt": "2021-07-08T15:29:35.892648Z",
            "updatedBy": "(unknown)",
            "updatedAt": "2021-07-08T15:29:35.892648Z",
            "propertyValues": [
                {
                    "id": 10,
                    "key": "position",
                    "value": "4"
                }
            ],
            "parentTermId": 45
        },
        {
            "id": 49,
            "label": "Smartphone",
            "description": "",
            "taxonomyId": 5,
            "publishStatus": "published",
            "createdBy": "(unknown)",
            "createdAt": "2021-07-08T15:32:54.656658Z",
            "updatedBy": "(unknown)",
            "updatedAt": "2021-07-08T15:32:54.656658Z",
            "propertyValues": [
                {
                    "id": 17,
                    "key": "position",
                    "value": "2"
                }
            ],
            "parentTermId": 42
        }
    ],
    "_links": {},
    "_page": {
        "size": 13,
        "totalElements": 13,
        "totalPages": 1,
        "number": 1
    }
}
```

## Create term
```shell
POST '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/terms'
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

In het pad geef je de `id` van de taxonomie waaraan je een term wenst toe te voegen.

Als payload geef je het volgende mee: 

```json
{
   "label": "winter",
   "description": "Lorum ipsum...",
   "publishStatus": "draft",
   "parentTermId": null,
   "propertyValues": [
       {
           "key": "position",
           "value": 1
       },
       {
           "key": "lang_label_nl",
           "value": "winter"
       },
       {
           "key": "lang_label_fr",
           "value": "hiver"
       },
       {
           "key": "externalRef",
           "value": "SF-98789-09"
       }
   ]
}
```

Waarbij 
* de `publishStatus` **draft** of **published** kan bevatten.
* om de term op het hoofdniveau te plaatsen geef je **null** mee voor de `parentTermId`
* Er zijn 3 bijkomende properties die je kan instellen: 
  * `position`: Bepaalt de plaats van deze term t.o.v. z’n broers/zussen (siblings)
  * `lang_label_<taal>`: Bepaalt de waarde van het `label` veld in de andere talen. 
  * `externalRef`: Een extra referentie veld, vrij te gebruiken.

## Update term
```shell
PUT '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/terms/{termid}'
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

In het pad geef je de `id` van de taxonomie.
In het pad geef je de `termid` van de term die je wenst aan te passen.

Als payload geef je het volgende mee: 
(In tegenstelling tot de create moet je hier `id` en `parentTermId` gelijk houden als je de term op de root wil behouden)

```json
{
   "id": 67,
   "label": "winter",
   "description": "Lorum ipsum...",
   "publishStatus": "draft",
   "parentTermId": 67,
   "propertyValues": [
       {
           "id": 223,
           "key": "position",
           "value": "1"
       },
       {
           "id": 267,
           "key": "lang_label_nl",
           "value": "winter"
       },
       {
           "id": 268,
           "key": "lang_label_fr",
           "value": "hiver"
       },
       {
           "id": 289,
           "key": "externalRef",
           "value": "SF-98789-09"
       }
   ]
}
```

## Volgorde veranderen
Gebruik deze functie om de volgorde van de termen aan te passen in de taxonomy. Je kan dit ook gebruiken om een aantal termen in één keer onder een andere term te plaatsen.

> Je kan kiezen om alle termen mee te geven of slechts een deel. In dit laatste geval moet je er zelf voor zorgen dat de volgorde correct blijft over alle termen heen en dat er bijvoorbeeld geen termen met dezelfde positie ontstaan. Of dat je hiërarchie fouten maakt zoals een kind dat eveneens z’n eigen ouder is.

```shell
PUT '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/terms/reorder'
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

In het pad geef je de `id` van de taxonomie.

Als payload geef je het volgende mee: 
```json
{
   "term-order": [
       {
           "id": 67,
           "parentId": null,
           "position": 1
       },
       {
           "id": 69,
           "parentId": 67,
           "position": 1
       },
       {
           "id": 73,
           "parentId": 67,
           "position": 2
       },
       {
           "id": 75,
           "parentId": null,
           "position": 2
       },
       {
           "id": 88,
           "parentId": null,
           "position": 3
       }
   ]
}
```

## Delete term
```shell
DELETE '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/terms/{termid}'
```

In het pad geef je de `id` van de taxonomie en de `termid` van de term dat je wenst te verwijderen.

