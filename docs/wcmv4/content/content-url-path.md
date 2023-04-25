# URL paths
Elk content item heeft in het `meta` luik een `urlPath` waarin informatie zit over het pad van dit content item. Het grote voordeel is dat frontends op die manier geen berekening moeten maken van het pad. 

[Haal je een content item op](/wcmv4/content/content-item-read) via bijvoorbeeld

```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/content?slug={slug}&lang={lang}
```

dan krijg je volgende payload. 

```json
 {
    "_id": "60b9f2a96729070009ad4a86",
    "fields": {
    },
    "meta": {
        ...
        "urlPath": {
            "nl": {
                "standardValue": "/info/hello-world",
                "standardPattern": "/info/[item:slug]",
                "pattern": "/info/[item:slug]",
                "value": "/info/hello-world"
            }
        }
        ...
    }
 }
```

De volledige absolute URL kan je opbouwen door url basis uit de [site info](/wcmv4/content/site) te combineren met deze urlPath values.

In de payload vind je:

* **standardPattern/standardValue:** dit is het patroon en de  waarde dat je normaal zou krijgen wat er [geconfigureerd](/redactie/content/inrichten-navigatie) is op het content type
* **pattern/value:** dit is het patroon en de waarde dat voor dit content item

## URL paden van gerelateerde content
Wil je van gerelateerde content ook een meta.urlPath meekrijgen dan ga je voorlopig een `populate=true` query parameter moeten hanteren. 

> Er is een [change](https://jira.antwerpen.be/browse/RED-1718) aangevraagd waarbij de paden altijd gaan meekomen en dat die by default worden gepopuleerd voor gerefereerde content. 
