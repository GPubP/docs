# URL paden 
Elk content item heeft in het `meta` luik een `urlPath` waarin informatie zit over het pad van dit content item.

Het grote voordeel is dat frontends op die manier geen berekening moeten maken van het pad. 

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

Het patroon wordt bepaald op het content type zelf tijdens de inrichting:

## URL paden van gerelateerde content
Wil je van gerelateerde content ook een meta.urlPath meekrijgen dan ga je voorlopig een `populate=true` query parameter moeten hanteren. 

> Er is een [change](https://jira.antwerpen.be/browse/RED-1718) aangevraagd waarbij de paden altijd gaan meekomen en dat die by default worden gepopuleerd voor gerefereerde content. 
