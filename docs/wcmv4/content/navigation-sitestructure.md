# Site structuur

Elke site heeft één sitestructuur per taal. wil je de lijst ophalen van alle site structuren gebruik je deze call via [het WCM Proxy endpoint](/wcmv4/content/endpoint-proxy): 

```shell
GET .../navigations/v1/sites/{siteId}/site-structures
```

Krijg je een output als volgt: 

```json
{
    "_links": { 
        ... 
    },
    "_embedded": {
        "resourceList": [
            {
                "id": 2159,
                "logicalId": "bb370b91-539e-4348-9b6c-610ed62a6c08",
                "label": "Sitestructuur",
                "description": "",
                "category": {
                    "id": 1614,
                    "label": "siteStructure_2aa630bc-8895-40cf-9c99-5416d856c66b_nl"
                },
                "publishStatus": "published",
                "createdBy": "Sys",
                "createdAt": "2022-10-04T09:07:22.671841Z",
                "updatedBy": "Sys",
                "updatedAt": "2022-10-04T09:07:22.671841Z",
                "slug": "sitestructuur-115",
                "meta": {
                    "lastEditor": null
                }
            }
        ]
    },
    "_page": {
        "number": 1,
        "size": 1,
        "totalElements": 1,
        "totalPages": 1
    }
}
```


Wil je één site structuur ophalen gebruik dan:
```shell
GET .../navigations/v1/sites/{siteId}/site-structures/{siteStructureId}
```

Zoals je kan zien in de output is de hiërarchie terug te vinden in de json payload: 
```json
{
    "id": 2159,
    "logicalId": "bb370b91-539e-4348-9b6c-610ed62a6c08",
    "label": "Sitestructuur",
    "description": "",
    "category": {
        "id": 1614,
        "label": "siteStructure_2aa630bc-8895-40cf-9c99-5416d856c66b_nl"
    },
    "publishStatus": "published",
    "items": [
        {
            "id": 141568,
            "treeId": 2159,
            "logicalId": "64b29d34-d914-4c29-9744-5248ef2f95c8",
            "label": "nieuws",
            "description": "",
            "publishStatus": "published",
            "weight": 11,
            "externalUrl": "",
            "slug": "nieuws-5",
            "items": [
                {
                    "id": 141570,
                    "treeId": 2159,
                    "logicalId": "eee3d71c-b2c8-4e88-af4b-606e6bc2a316",
                    "label": "EL - Nieuwsbericht",
                    "description": "Maak een kort nieuwsbericht aan",
                    "publishStatus": "published",
                    "weight": 1,
                    "externalUrl": "",
                    "externalReference": "1f8835e6-f2ef-450a-aaff-6a5cab3f563b",
                    "slug": "el_nieuwsbericht"
                }
            ]
        },
        {
            "id": 141574,
            "treeId": 2159,
            "logicalId": "e7c94786-d488-494e-a715-abdc4395f9d3",
            "label": "test 1",
            "description": "Beschrijving",
            "publishStatus": "draft",
            "weight": 14,
            "externalUrl": "https://www.pizzaslicer.be/activiteit/test-1",
            "externalReference": "ca561c9b-01be-4e31-9c26-236585c7afcc",
            "slug": "test-1"
        },
        {
            "id": 141579,
            "treeId": 2159,
            "logicalId": "14b21fce-2fab-4f32-ac62-f542fe09bec7",
            "label": "dienstverlening",
            "description": "dienstverlening",
            "publishStatus": "published",
            "weight": 17,
            "externalUrl": "",
            "slug": "dienstverlening-2",
            "items": [
                {
                    "id": 141580,
                    "treeId": 2159,
                    "logicalId": "e926ca27-f1a1-4c2c-a9b5-a9ec2126e5ae",
                    "label": "preventie",
                    "description": "preventie",
                    "publishStatus": "published",
                    "weight": 0,
                    "externalUrl": "",
                    "slug": "preventie-1",
                    "items": [
                        {
                            "id": 141581,
                            "treeId": 2159,
                            "logicalId": "4dcb67b5-ec38-4c8a-80ff-00fb6504d5c4",
                            "label": "test 1",
                            "description": "test 1",
                            "publishStatus": "draft",
                            "weight": 0,
                            "externalUrl": "https://www.pizzaslicer.be/activiteit/test-1",
                            "externalReference": "ca561c9b-01be-4e31-9c26-236585c7afcc",
                            "slug": "test-1"
                        }
                    ]
                }
            ]
        }
    ],
    "createdBy": "Sys",
    "createdAt": "2022-10-04T09:07:22.671841Z",
    "updatedBy": "Sys",
    "updatedAt": "2022-10-04T09:07:22.671841Z",
    "slug": "sitestructuur-115",
    "itemCount": 6,
    "meta": {
        "lastEditor": null
    }
}
```

Bovenstaande calls (en nog andere) vertrekken vanuit de sitestructuur zelf. Wil je vertrekken vanuit één content item en informatie daarover in de sitestructuur, dan kan je gebruikmaken van onderstaande calls. 

!> Todo: add api calls

## Primaire versus secundaire plaatsen 
In de sitestructuur staat elk content item maar op één primaire plaats en mogelijk op meerdere secundaire plaatsen. De primaire plaats, de hoofdplaats; is degene die gebruikt wordt om het [broodkruimel](/wcmv4/content/navigation-breadcrumb) op te bepalen. 

Anderzijds zijn er frontends die een overzichtspagina toont met een tegeltje erop voor elk kind-pagina. Heel af en toe wil men een pagina op verschillende overzichten plaatsen waardoor hetzelfde content item dus onder 2 ouders hangt. Zonder meer is het dan moeilijk om te bepalen wat het broodkruimelpad is. Vandaar dat we de primaire registratie gebruiken om dit pad te bepalen en toch toelaten om content items meerdere keren in de structuur te plaatsen.

Hieronder zie je dat het content item `xyz` twee keer geregistreerd is in de boomstructuur, onder zowel `info` als `jobs`. De registratie onder info is de primaire registratie.

![Site structuur](../assets/navigation-sitestructure.jpg 'Primaire registraties')


Je kan via de API de primaire registratie ophalen via: 

```shell
GET .../proxy/public/navigations/v1/sites/{siteId}/content/{contentId}/site-structure-primary-item
```

met deze onderstaande payload  

```json
{
    "id": 141583,
    "treeId": 2159,
    "logicalId": "28367365-72bf-431e-9935-cd3e7edb8a99",
    "parentId": 141580,
    "label": "sitestructuur-test",
    "description": "sitestructuur-test",
    "externalUrl": "https://www.pizzaslicer.be/activiteit/sitestructuur-test",
    "publishStatus": "published",
    "weight": 2,
    "parents": [...],
    "slug": "sitestructuur-test",
    "externalReference": "88f1115d-334d-4130-8244-e1e2987e3acf",
    "properties": {
        "type": "primary"
    }
}
```

## De verschillende soorten structuurelementen
Elk element in de sitestructuur heeft een `properties` verzameling met daarin een type. Dit kan één van de volgende waardes bevatten:

* **primary**: hiermee herken je de primaire plaats van een content item in de sitestructuur.
* **secondary**: hiermee herken je de secundaire registraties van dit content item in de sitestructuur
* **section**: dit type wordt gebruikt wanneer een redacteur een tussentitel in de sitestructuur toevoegt, zeg maar een element in de boomstructuur wat als titel fungeert en dus niet met een content item geassocieerd is. 
* **external**: dit type geeft aan dat er een externe url (naar een andere site) geregistreerd is op deze plaats in de sitestructuur. 