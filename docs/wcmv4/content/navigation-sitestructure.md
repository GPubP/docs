# Site structuur

Redacteurs maken content items en ‘hangen’ deze in een boomstructuur aka sitestructuur. Typisch worden pagina's in een sitestructuur gegoten voor:

1. Op een overzicht pagina kan er een lijst getoond worden van onderliggende pagina's
2. [Broodkruimels](/wcmv4/content/navigation-breadcrumb) kunnen opgebouwd worden a.d.h.v. de plaats in de sitestructuur.

Er is maar één sitestructuur per site en per taal.

Op deze pagina vind je: 

* [Sitestructuren per site](/wcmv4/content/navigation-sitestructure?id=sitestructuren-per-site)
* [Sitestructuur details](/wcmv4/content/navigation-sitestructure?id=sitestructuur-details)
  * [Hiërarchisch lijst ophalen](/wcmv4/content/navigation-sitestructure?id=hiërarchisch-lijst-ophalen)
  * [Vlakke lijst ophalen](/wcmv4/content/navigation-sitestructure?id=vlakke-lijst-ophalen)
  * [Details van één sitestructuur element](/wcmv4/content/navigation-sitestructure?id=details-van-één-sitestructuur-element)
* [Primaire versus secundaire plaatsen](/wcmv4/content/navigation-sitestructure?id=primaire-versus-secundaire-plaatsen)
* [Haal de kinderen op van een content item](/wcmv4/content/navigation-sitestructure?id=haal-de-kinderen-op-van-een-content-item)
* [De verschillende soorten structuurelementen](/wcmv4/content/navigation-sitestructure?id=de-verschillende-soorten-structuurelementen)

## Sitestructuren per site

Wil je de lijst ophalen van alle site structuren voor je site, gebruik je deze call via [het WCM Proxy endpoint](/wcmv4/content/endpoint-proxy): 

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
## Sitestructuur details

Er zijn 2 manieren om een sitestructuur op te halen: 

1. [Hiërarchisch](/wcmv4/content/navigation-sitestructure?id=hiërarchisch-lijst-ophalen), deze is compacter en de json output volgt de hiërarchie
2. [Vlakke lijst](/wcmv4/content/navigation-sitestructure?id=vlakke-lijst-ophalen), deze is uitgebreider met o.a. het [soort structuurelement](/wcmv4/content/navigation-sitestructure?id=de-verschillende-soorten-structuurelementen)


### Hiërarchisch lijst ophalen

Wil je de details ophalen van één site structuur gebruik dan:
```shell
GET .../navigations/v1/sites/{siteId}/site-structures/{siteStructureId}
```

Zoals je kan zien in de output is de hiërarchie terug te vinden in de json payload: 
```json
{
    "id": 2159,
    "logicalId": "bb370b91-539e-4348-9b6c-610ed62a6c08",
    "label": "Sitestructuur EL - pizza slicer",
    "description": "todo",
    "category": {
        "id": 1614,
        "label": "siteStructure_2aa630bc-8895-40cf-9c99-5416d856c66b_nl"
    },
    "publishStatus": "published",
    "items": [
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
                    "slug": "preventie-1"
                }
            ]
        },
        {
            "id": 141680,
            "treeId": 2159,
            "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
            "label": "test-level-1",
            "description": "test-level-1",
            "publishStatus": "published",
            "weight": 19,
            "externalUrl": "",
            "slug": "test-level-1",
            "items": [
                {
                    "id": 141681,
                    "treeId": 2159,
                    "logicalId": "2a60a857-00d6-40a8-82ea-27657def6cba",
                    "label": "test-level-1.1",
                    "description": "test-level-1.1",
                    "publishStatus": "published",
                    "weight": 0,
                    "externalUrl": "",
                    "slug": "test-level-1.1"
                },
                {
                    "id": 141682,
                    "treeId": 2159,
                    "logicalId": "edd0970d-e501-4be5-9870-037bef7dcbf0",
                    "label": "test-level-1.2",
                    "description": "test-level-1.2",
                    "publishStatus": "published",
                    "weight": 1,
                    "externalUrl": "",
                    "slug": "test-level-1.2",
                    "items": [
                        {
                            "id": 141683,
                            "treeId": 2159,
                            "logicalId": "49cae1fa-454d-4b1f-9ec4-579cdda427f6",
                            "label": "test-level-1.2.1",
                            "description": "test-level-1.2.1",
                            "publishStatus": "published",
                            "weight": 0,
                            "externalUrl": "",
                            "slug": "test-level-1.2.1",
                            "items": [
                                {
                                    "id": 141684,
                                    "treeId": 2159,
                                    "logicalId": "a21fa2b3-0ac4-44a6-83e6-346cf2900979",
                                    "label": "test-level-1.2.1.1",
                                    "description": "test-level-1.2.1.1",
                                    "publishStatus": "published",
                                    "weight": 0,
                                    "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1",
                                    "externalReference": "50a2cc63-76d7-4e29-ba8c-becfc3f8355b",
                                    "slug": "test-level-1.2.1.1",
                                    "items": [
                                        {
                                            "id": 141685,
                                            "treeId": 2159,
                                            "logicalId": "eddda643-2b6d-4f94-82be-81182cd8e9a4",
                                            "label": "test-level-1.2.1.1.1",
                                            "description": "test-level-1.2.1.1.1",
                                            "publishStatus": "published",
                                            "weight": 0,
                                            "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1.1",
                                            "externalReference": "1f9eb949-9eb7-4e3d-bd6f-4b57b8c6f84a",
                                            "slug": "test-level-1.2.1.1.1"
                                        },                                        
                                        {
                                            "id": 141685,
                                            "treeId": 2159,
                                            "logicalId": "d98d4db6-f74c-4928-aabe-640524fed338",
                                            "label": "test-level-1.2.1.1.2",
                                            "description": "test-level-1.2.1.1.2",
                                            "publishStatus": "published",
                                            "weight": 0,
                                            "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1.2",
                                            "externalReference": "b7b307f8-b5a0-490c-a038-312822842732",
                                            "slug": "test-level-1.2.1.1.2"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ],
    "slug": "sitestructuur-el-pizza-slicer",
    "itemCount": 12,
    ...
}
```

### Vlakke lijst ophalen

Alternatief voor het ophalen van de sitestructuur op [hiërarchische](/wcmv4/content/navigation-sitestructure?id=hiërarchisch-lijst-ophalen) wijze kan je de lijst ook vlak ophalen: 

```shell
GET .../navigations/v1/sites/{siteId}/site-structures/{siteStructureId}/items
```

Zoals je kan zien in de output is de hiërarchie terug te vinden in de json payload: 
```json
{
    "_links": {
        "first": {
            "href": "https://api-gw-a.antwerpen.be/trees/2159/items?page=1&pagesize=10"
        },
        "self": {
            "href": "https://api-gw-a.antwerpen.be/trees/2159/items?page=1&pagesize=10"
        },
        "last": {
            "href": "https://api-gw-a.antwerpen.be/trees/2159/items?page=2&pagesize=10"
        }
    },
    "_embedded": {
        "resourceList": [
            {
                "id": 141580,
                "treeId": 2159,
                "logicalId": "e926ca27-f1a1-4c2c-a9b5-a9ec2126e5ae",
                "parentId": 141579,
                "label": "preventie",
                "description": "preventie",
                "externalUrl": "",
                "publishStatus": "published",
                "weight": 0,
                "parents": [
                    {
                        "id": 141579,
                        "treeId": 2159,
                        "logicalId": "14b21fce-2fab-4f32-ac62-f542fe09bec7",
                        "label": "dienstverlening",
                        "description": "dienstverlening",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 17,
                        "slug": "dienstverlening"
                    }
                ],
                "slug": "preventie-1",
                "properties": {
                    "type": "section"
                }
            },
            {
                "id": 141681,
                "treeId": 2159,
                "logicalId": "2a60a857-00d6-40a8-82ea-27657def6cba",
                "parentId": 141680,
                "label": "test-level-1.1",
                "description": "test-level-1.1",
                "externalUrl": "",
                "publishStatus": "published",
                "weight": 0,
                "parents": [
                    {
                        "id": 141680,
                        "treeId": 2159,
                        "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
                        "label": "test-level-1",
                        "description": "test-level-1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 19,
                        "slug": "test-level-1"
                    }
                ],
                "slug": "test-level-1.1",
                "properties": {
                    "type": "section"
                }
            },
            {
                "id": 141683,
                "treeId": 2159,
                "logicalId": "49cae1fa-454d-4b1f-9ec4-579cdda427f6",
                "parentId": 141682,
                "label": "test-level-1.2.1",
                "description": "test-level-1.2.1",
                "externalUrl": "",
                "publishStatus": "published",
                "weight": 0,
                "parents": [
                    {
                        "id": 141680,
                        "treeId": 2159,
                        "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
                        "label": "test-level-1",
                        "description": "test-level-1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 19,
                        "slug": "test-level-1"
                    },
                    {
                        "id": 141682,
                        "treeId": 2159,
                        "logicalId": "edd0970d-e501-4be5-9870-037bef7dcbf0",
                        "parentId": 141680,
                        "label": "test-level-1.2",
                        "description": "test-level-1.2",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 1,
                        "slug": "test-level-1.2"
                    }
                ],
                "slug": "test-level-1.2.1",
                "properties": {
                    "type": "section"
                }
            },
            {
                "id": 141684,
                "treeId": 2159,
                "logicalId": "a21fa2b3-0ac4-44a6-83e6-346cf2900979",
                "parentId": 141683,
                "label": "test-level-1.2.1.1",
                "description": "test met axel",
                "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1",
                "publishStatus": "published",
                "weight": 0,
                "parents": [
                    {
                        "id": 141680,
                        "treeId": 2159,
                        "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
                        "label": "test-level-1",
                        "description": "test-level-1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 19,
                        "slug": "test-level-1"
                    },
                    {
                        "id": 141682,
                        "treeId": 2159,
                        "logicalId": "edd0970d-e501-4be5-9870-037bef7dcbf0",
                        "parentId": 141680,
                        "label": "test-level-1.2",
                        "description": "test-level-1.2",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 1,
                        "slug": "test-level-1.2"
                    },
                    {
                        "id": 141683,
                        "treeId": 2159,
                        "logicalId": "49cae1fa-454d-4b1f-9ec4-579cdda427f6",
                        "parentId": 141682,
                        "label": "test-level-1.2.1",
                        "description": "test-level-1.2.1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 0,
                        "slug": "test-level-1.2.1"
                    }
                ],
                "slug": "test-level-1.2.1.1",
                "externalReference": "50a2cc63-76d7-4e29-ba8c-becfc3f8355b",
                "properties": {
                    "type": "primary"
                }
            },
            {
                "id": 141685,
                "treeId": 2159,
                "logicalId": "eddda643-2b6d-4f94-82be-81182cd8e9a4",
                "parentId": 141684,
                "label": "test-level-1.2.1.1.1",
                "description": "",
                "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1.1",
                "publishStatus": "published",
                "weight": 0,
                "parents": [
                    {
                        "id": 141680,
                        "treeId": 2159,
                        "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
                        "label": "test-level-1",
                        "description": "test-level-1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 19,
                        "slug": "test-level-1"
                    },
                    {
                        "id": 141682,
                        "treeId": 2159,
                        "logicalId": "edd0970d-e501-4be5-9870-037bef7dcbf0",
                        "parentId": 141680,
                        "label": "test-level-1.2",
                        "description": "test-level-1.2",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 1,
                        "slug": "test-level-1.2"
                    },
                    {
                        "id": 141683,
                        "treeId": 2159,
                        "logicalId": "49cae1fa-454d-4b1f-9ec4-579cdda427f6",
                        "parentId": 141682,
                        "label": "test-level-1.2.1",
                        "description": "test-level-1.2.1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 0,
                        "slug": "test-level-1.2.1"
                    },
                    {
                        "id": 141684,
                        "treeId": 2159,
                        "logicalId": "a21fa2b3-0ac4-44a6-83e6-346cf2900979",
                        "parentId": 141683,
                        "label": "test-level-1.2.1.1",
                        "description": "test-level-1.2.1.1",
                        "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1",
                        "publishStatus": "published",
                        "weight": 0,
                        "slug": "test-level-1.2.1.1",
                        "externalReference": "50a2cc63-76d7-4e29-ba8c-becfc3f8355b"
                    }
                ],
                "slug": "test-level-1.2.1.1.1",
                "externalReference": "1f9eb949-9eb7-4e3d-bd6f-4b57b8c6f84a",
                "properties": {
                    "type": "primary"
                }
            },
            {
                "id": 141682,
                "treeId": 2159,
                "logicalId": "edd0970d-e501-4be5-9870-037bef7dcbf0",
                "parentId": 141680,
                "label": "test-level-1.2",
                "description": "test-level-1.2",
                "externalUrl": "",
                "publishStatus": "published",
                "weight": 1,
                "parents": [
                    {
                        "id": 141680,
                        "treeId": 2159,
                        "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
                        "label": "test-level-1",
                        "description": "test-level-1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 19,
                        "slug": "test-level-1"
                    }
                ],
                "slug": "test-level-1.2",
                "properties": {
                    "type": "section"
                }
            },
            {
                "id": 141686,
                "treeId": 2159,
                "logicalId": "5a741685-44c6-4c48-94db-897490cf2a8f",
                "parentId": 141684,
                "label": "test-level-1.2.1.1.2",
                "description": "",
                "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1.2",
                "publishStatus": "published",
                "weight": 1,
                "parents": [
                    {
                        "id": 141680,
                        "treeId": 2159,
                        "logicalId": "aae24678-ed57-443b-87bd-2de3377374f3",
                        "label": "test-level-1",
                        "description": "test-level-1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 19,
                        "slug": "test-level-1"
                    },
                    {
                        "id": 141682,
                        "treeId": 2159,
                        "logicalId": "edd0970d-e501-4be5-9870-037bef7dcbf0",
                        "parentId": 141680,
                        "label": "test-level-1.2",
                        "description": "test-level-1.2",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 1,
                        "slug": "test-level-1.2"
                    },
                    {
                        "id": 141683,
                        "treeId": 2159,
                        "logicalId": "49cae1fa-454d-4b1f-9ec4-579cdda427f6",
                        "parentId": 141682,
                        "label": "test-level-1.2.1",
                        "description": "test-level-1.2.1",
                        "externalUrl": "",
                        "publishStatus": "published",
                        "weight": 0,
                        "slug": "test-level-1.2.1"
                    },
                    {
                        "id": 141684,
                        "treeId": 2159,
                        "logicalId": "a21fa2b3-0ac4-44a6-83e6-346cf2900979",
                        "parentId": 141683,
                        "label": "test-level-1.2.1.1",
                        "description": "test-level-1.2.1.1",
                        "externalUrl": "https://www.pizzaslicer.be/info/test-level-1.2.1.1",
                        "publishStatus": "published",
                        "weight": 0,
                        "slug": "test-level-1.2.1.1",
                        "externalReference": "50a2cc63-76d7-4e29-ba8c-becfc3f8355b"
                    }
                ],
                "slug": "sub-item-2",
                "externalReference": "b24d3526-e2ea-4178-afa6-fb505df3ac58",
                "properties": {
                    "type": "primary"
                }
            }
        ]
    },
    "_page": {
        "number": 1,
        "size": 10,
        "totalElements": 12,
        "totalPages": 2
    }
}
```

### Details van één sitestructuur element

Wil je de informatie van één element uit de sitestructuur halen dan gebruik je: 

```shell
GET .../navigations/v1/sites/{siteId}/site-structures/{siteStructureId}/items/{itemId}
```

Met als payload:

```json
{
    "id": 141580,
    "treeId": 2159,
    "logicalId": "e926ca27-f1a1-4c2c-a9b5-a9ec2126e5ae",
    "parentId": 141579,
    "label": "preventie",
    "description": "preventie",
    "externalUrl": "",
    "publishStatus": "published",
    "weight": 0,
    "slug": "preventie",
    "properties": {
        "type": "section"
    }
}
```

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

## Haal de kinderen op van een content item
Vaak wil je in de frontend een pagina tonen met inhoud en een overzicht van alle pagina's die 'eronder hangen', zeg maar de kinderen van die pagina. Op deze manier kan men grote luiken content opdelen in hoofd en sub pagina's. 

> [!WARNING|label:Belangrijk]
> Belangrijk om hier te onthouden is dat onderstaande call een lijst van sub pagina's geeft van zowel [primaire als secundaire registraties](/wcmv4/content/navigation-sitestructure?id=primaire-versus-secundaire-plaatsen) in de boom. Dat je hier ook de secundaire registraties krijgt is één van de bestaansredenen van dit concept. Vaak heb je een pagina ergens in de boomstructuur hangen waarop de [broodkruimel](/wcmv4/content/navigation-breadcrumb) gebasseerd wordt. Daarnaast wil je dat diezelfde pagina ook kan verschijnen op andere overzicht pagina's. De plaatsen waar je het nog wil laten verschijnen zijn dan de secundaire registraties.

```shell
GET .../proxy/public/navigations/v1/sites/{siteId}/content/{contentId}/subset
```

met deze onderstaande payload waarbij je het gevraagd content item krijgt met z'n kinderen: 

```json
{
    "_links": {
        "first": {
            "href": "https://api-gw-a.antwerpen.be/trees/2159/subset?page=1&pagesize=10"
        },
        "self": {
            "href": "https://api-gw-a.antwerpen.be/trees/2159/subset?page=1&pagesize=10"
        },
        "last": {
            "href": "https://api-gw-a.antwerpen.be/trees/2159/subset?page=1&pagesize=10"
        }
    },
    "_embedded": {
        "resourceList": [
            {
                "id": 141684,
                "treeId": 2159,
                "logicalId": "a21fa2b3-0ac4-44a6-83e6-346cf2900979",
                "parentId": 141683,
                "label": "main page",
                "description": "main page",
                "externalUrl": "https://www.pizzaslicer.be/info/main-page",
                "publishStatus": "published",
                "weight": 0,
                "items": [
                    {
                        "id": 141685,
                        "treeId": 2159,
                        "logicalId": "eddda643-2b6d-4f94-82be-81182cd8e9a4",
                        "parentId": 141684,
                        "label": "sub item 1",
                        "description": "",
                        "externalUrl": "https://www.pizzaslicer.be/info/sub-item-1",
                        "publishStatus": "published",
                        "weight": 0,
                        "slug": "sub-item-1",
                        "externalReference": "1f9eb949-9eb7-4e3d-bd6f-4b57b8c6f84a",
                        "properties": {
                            "type": "primary"
                        }
                    },
                    {
                        "id": 141686,
                        "treeId": 2159,
                        "logicalId": "5a741685-44c6-4c48-94db-897490cf2a8f",
                        "parentId": 141684,
                        "label": "sub item 2",
                        "description": "",
                        "externalUrl": "https://www.pizzaslicer.be/info/sub-item-2",
                        "publishStatus": "published",
                        "weight": 1,
                        "slug": "sub-item-2",
                        "externalReference": "b24d3526-e2ea-4178-afa6-fb505df3ac58",
                        "properties": {
                            "type": "primary"
                        }
                    }
                ],
                "slug": "main-page",
                "externalReference": "50a2cc63-76d7-4e29-ba8c-becfc3f8355b",
                "properties": {
                    "type": "primary"
                }
            }
        ]
    },
    "_page": {
        "number": 1,
        "size": 1,
        "totalElements": 2,
        "totalPages": 1
    }
}
```


## De verschillende soorten structuurelementen
Elk element in de sitestructuur heeft een `properties` verzameling met daarin een `type` property. Dit kan één van de volgende waardes bevatten:

* **primary**: hiermee herken je de [primaire plaats](/wcmv4/content/navigation-sitestructure?id=primaire-versus-secundaire-plaatsen) van een content item in de sitestructuur.
* **secondary**: hiermee herken je de [secundaire registraties](/wcmv4/content/navigation-sitestructure?id=primaire-versus-secundaire-plaatsen) van dit content item in de sitestructuur
* **section**: dit type wordt gebruikt wanneer een redacteur een tussentitel in de sitestructuur toevoegt, zeg maar een element in de boomstructuur wat als titel fungeert en dus niet met een content item geassocieerd is. 
* **external**: dit type geeft aan dat er een externe url (naar een andere site) geregistreerd is op deze plaats in de sitestructuur. 