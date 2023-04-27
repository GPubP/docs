# Menu's

Redacteurs maken één of meerdere menu’s die ze gebruiken als hoofdmenu, als footer menu e.d. In essentie is een menu ook een hiërarchische structuur van nodes. Een node kan ofwel
*  een tussentitel zijn, 
*  een verwijzing naar een content item of 
*  een verwijzing naar een externe pagina (url).

Met deze API call via het [WCM Proxy endpoint](/wcmv4/content/endpoint-proxy) haal je alle menu’s op:

```shell
GET .../navigations/v1/sites/{siteId}/menus
```

Met deze payload:

```json
{
    "_links": { ... },
    "_embedded": {
        "resourceList": [
            {
                "id": 2169,
                "logicalId": "18b8bd4a-27fc-45d9-890b-14ca463ee82f",
                "label": "Hoofdmenu",
                "description": "Om te gebruiken aan de bovenzijde van de site",
                "category": {
                    "id": 1605,
                    "label": "menu_2aa630bc-8895-40cf-9c99-5416d856c66b_generic"
                },
                "publishStatus": "published",
                "createdBy": "Sys",
                "createdAt": "2022-11-19T14:59:56.101853Z",
                "updatedBy": "Sys",
                "updatedAt": "2022-11-19T14:59:56.101854Z",
                "slug": "hoofdmenu-14",
                "meta": {
                    "lastEditor": "a0c55f11-a545-48c8-a1ee-4a5e2ce9a1f7"
                }
            },
            {
                "id": 2170,
                "logicalId": "c8b6a362-7086-484e-986e-e02e6df68875",
                "label": "Deurmat menu",
                "description": "Om te gebruiken in de deurmat van de site",
                "category": {
                    "id": 1605,
                    "label": "menu_2aa630bc-8895-40cf-9c99-5416d856c66b_generic"
                },
                "publishStatus": "published",
                "createdBy": "Sys",
                "createdAt": "2022-11-19T15:03:50.173873Z",
                "updatedBy": "Sys",
                "updatedAt": "2022-11-19T15:03:50.173903Z",
                "slug": "deurmat-menu",
                "meta": {
                    "lastEditor": "a0c55f11-a545-48c8-a1ee-4a5e2ce9a1f7"
                }
            }
        ]
    },
    "_page": {
        "number": 1,
        "size": 2,
        "totalElements": 2,
        "totalPages": 1
    }
}
```

Wil je één menu ophalen, krijg je een hiërarchie terug. 

```shell
GET .../navigations/v1/sites/{siteId}/menus/{menuId}
```

Met deze payload:

```json
{
    "id": 2169,
    "logicalId": "18b8bd4a-27fc-45d9-890b-14ca463ee82f",
    "label": "Hoofdmenu",
    "description": "Om te gebruiken aan de bovenzijde van de site",
    "category": {
        "id": 1605,
        "label": "menu_2aa630bc-8895-40cf-9c99-5416d856c66b_generic"
    },
    "publishStatus": "published",
    "items": [
        {
            "id": 141585,
            "treeId": 2169,
            "logicalId": "7ea537c9-4cb4-4371-b47f-a72885a0fa5e",
            "label": "Een tussentitel",
            "description": "voorbeeld tussentitel",
            "publishStatus": "published",
            "weight": 0,
            "externalUrl": "",
            "slug": "een-tussentitel",
            "items": [
                {
                    "id": 141587,
                    "treeId": 2169,
                    "logicalId": "8386dbf9-210e-471c-a13c-eb1637cddefa",
                    "label": "sitestructuur-test",
                    "description": "een content referentie",
                    "publishStatus": "published",
                    "weight": 0,
                    "externalUrl": "https://www.pizzaslicer.be/activiteit/sitestructuur-test",
                    "externalReference": "88f1115d-334d-4130-8244-e1e2987e3acf",
                    "slug": "sitestructuur-test"
                }
            ]
        },
        {
            "id": 141586,
            "treeId": 2169,
            "logicalId": "8134f8f6-b3c2-473c-9051-25043044bf8e",
            "label": "Google",
            "description": "een externe url",
            "publishStatus": "published",
            "weight": 1,
            "externalUrl": "https://www.google.be",
            "slug": "google-2"
        }
    ],
    "createdBy": "Sys",
    "createdAt": "2022-11-19T14:59:56.101853Z",
    "updatedBy": "Sys",
    "updatedAt": "2022-11-19T14:59:56.101854Z",
    "slug": "hoofdmenu-14",
    "itemCount": 3,
    "meta": {
        "lastEditor": {
            "address": null,
            "domain": "ICA",
            "email": "Erik.Lenaerts@digipolis.be",
            "externalMutableReference": "ex02536@digant.antwerpen.local",
            "firstname": "Erik",
            "id": "a0c55f11-a545-48c8-a1ee-4a5e2ce9a1f7",
            "lastname": "Lenaerts",
            "nickname": null,
            "type": "mprofiel",
            "username": "ex02536"
        }
    }
}
```

Zoals je kan zien is het een hiërarchie waarbij elke node een items array heeft met daarin de kinderen. 

Haal je de detail op van één menu item 
```shell
GET .../navigations/v1/sites/[siteId]/menus/[menuId]/items[menuItemId]
```

dan krijg je:

```json
{
    "id": 141587,
    "treeId": 2169,
    "logicalId": "8386dbf9-210e-471c-a13c-eb1637cddefa",
    "parentId": 141585,
    "label": "sitestructuur-test",
    "description": "een content referentie",
    "externalUrl": "https://www.pizzaslicer.be/activiteit/sitestructuur-test",
    "publishStatus": "published",
    "weight": 0,
    "slug": "sitestructuur-test",
    "externalReference": "88f1115d-334d-4130-8244-e1e2987e3acf",
    "properties": {
        "type": "internal"
    }
}
```

## De verschillende soorten menu elementen
Net zoals bij site structuur bevat elke node in de hiërarchie een properties verzameling met hierin een type: 

* **internal**: dit geeft aan dat dit element in de boomstructuur verwijst naar een content item, zeg maar een interne link.
* **section**: dit type wordt gebruikt wanneer een redacteur een tussentitel in het menu toevoegt
* **external**: dit type geeft aan dat er een externe url (naar een andere site) geregistreerd is op deze plaats in het menu 

Als je vertrekt vanuit een content item zelf, kan je 

```shell
GET .../navigations/v1/sites/[siteId]/content/[contentId]/menu-items
```

met deze payload:

!> todo, momenteel nog een issue hiermee (RED-2848)


Andere calls zijn: 

.../navigations/v1/sites/[siteId]/menus/[menuId]/items
.../navigations/v1/sites/[siteId]/menus/[menuId]/items/[itemId]
.../navigations/v1/sites/[siteId]/menus/[menuId]/subset

