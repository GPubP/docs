# Site API

## Site informatie opvragen

Via de WCM kan je site informatie opvragen. Gebruik hiervoor de volgende API call:

```shell
GET /wcm-proxy/v4/sites/v1/sites/{id}'
```

De output is als volgt. Hier vind je onder andere de geconfigureerd [content types](/redactie/content/inrichten-content-types) en [talen](/redactie/content/inrichten-meertaligheid). Vooral de `data.url` waarde is belangrijk voor afnemers, deze vormt de basis voor de [url paden](/wcmv4/content/content-url-path).

```json
{
    "data": {
        "contentTypes": [
            "63358e89b1760f00072cd83b",
            "6388bf985168eb00077c4685",
            "6388dd20f4b17600076f0cb6",
            "6447c7cedfdca80007babc81"
        ],
        "languages": [
            "nl"
        ],
        "name": "EL - pizza slicer",
        "description": "EL - pizza slicer",
        "url": {
            "nl": "https://www.pizzaslicer.be",
            "fr": "https://www.pizzaslicer.be",
            "en": "https://www.pizzaslicer.be",
            "multiLanguage": true
        },
        "modulesConfig": [
            {
                "uuid": "d039af53-ea6f-44e8-8e8f-6e0b7342a583",
                "name": "search",
                "label": "Elastic App Search",
                "config": {
                    "allowSearch": true,
                    "urlPattern": {
                        "multiLanguage": true,
                        "nl": "[site:url]/assets/[asset:uuid]"
                    }
                }
            },
            {
                "uuid": "4a508d8b-db78-4466-b4a1-181187b7d991",
                "name": "navigation",
                "label": "Navigatie",
                "config": {
                    "allowSiteStructure": true,
                    "allowMenus": true
                }
            }
        ]
    },
    "meta": {
        "active": true,
        "deleted": false,
        "tenant": "tenant-test-4",
        "lastEditor": {
            ...
        },
        "createdAt": "2022-07-21T12:42:41.435Z",
        "updatedAt": "2023-04-25T12:30:14.429Z"
    },
    "uuid": "2aa630bc-8895-40cf-9c99-5416d856c66b"
}
```