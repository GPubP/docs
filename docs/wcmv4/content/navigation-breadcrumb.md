# Broodkruimel

Als je van een content item het broodkruimelpad wil opvragen dan kan je gebruik maken van onderstaande call via [het WCM Proxy endpoint](/wcmv4/content/endpoint-proxy):

```shell
GET .../navigations/v1/sites/{siteId}/content/{contentId}/breadcrumbs
```

Met deze payload:

```json
{
    "_links": { ...  },
    "_embedded": {
        "resourceList": [
            {
                "id": 141579,
                "treeId": 2159,
                "logicalId": "14b21fce-2fab-4f32-ac62-f542fe09bec7",
                "label": "dienstverlening",
                "description": "dienstverlening",
                "externalUrl": "https://www.pizzaslicer.be/dienstverlening",
                "publishStatus": "published",
                "weight": 17,
                "parents": [ ... ],
                "slug": "dienstverlening",
                "properties": {
                    "type": "section"
                },                
                "items": [
                    {
                        "id": 141580,
                        "treeId": 2159,
                        "logicalId": "e926ca27-f1a1-4c2c-a9b5-a9ec2126e5ae",
                        "parentId": 141579,
                        "label": "preventie",
                        "description": "preventie",
                        "externalUrl": "https://www.pizzaslicer.be/dienstverlening/preventie",
                        "publishStatus": "published",
                        "weight": 0,
                        "parents": [ ... ],
                        "slug": "preventie",
                        "properties": {
                            "type": "section"
                        },
                        "items": [
                            {
                                "id": 141581,
                                "treeId": 2159,
                                "logicalId": "aa26ca27-f1a1-4c2c-a9b5-a9ec2126e5bb",
                                "parentId": 141580,
                                "label": "verkeer",
                                "description": "verkeer",
                                "externalUrl": "https://www.pizzaslicer.be/dienstverlening/preventie/verkeer",
                                "publishStatus": "published",
                                "weight": 0,
                                "parents": [ ... ],
                                "slug": "verkeer",
                                "properties": {
                                    "type": "section"
                                }
                            }
                    }
                ]
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

Je zal merken dat de broodkruimel begint vanaf de root met dan het eerste element `dienstverlening` in de resourceList en in de items collectie ervan zit het kind `preventie`. In dit geval kan je de broodkruimel als volgt opbouwen:

1. Haal de [root url op van je site](/wcmv4/content/site), je krijgt bijvoorbeeld:

   Home = <https://www.pizzaslicer.be>

2. haal het `label` en de `externalUrl` op van het eerste segment dat je vind als eerste in de `resourceList`. Voeg de **slug** toe aan de root, je voorbeeld wordt dan:

   Home > dienstverlening = <https://www.pizzaslicer.be/dienstverlening>

3. haal het `label` en de `externalUrl` op van het volgende segment in de `items` array.

   Home > dienstverlening > preventie = <https://www.pizzaslicer.be/dienstverlening/preventie>

4. Herhaal stap 3 tot er geen onderliggende items meer zijn.

   Home > dienstverlening > preventie > verkeer = <https://www.pizzaslicer.be/dienstverlening/preventie/verkeer>

> [!WARNING|label:Opmerking]
> Het gevraagde content item, o.b.v. de `contentId` in de API call, zit **niet** mee in de broodkruimel.
