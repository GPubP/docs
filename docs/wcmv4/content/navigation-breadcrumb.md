# Broodkruimel

Als je van een content item het broodkruimelpad wil opvragen dan kan je gebruik maken van onderstaande call: 

```shell
GET .../proxy/public/navigations/v1/sites/{siteId}/content/{contentId}/breadcrumbs
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
                "externalUrl": "",
                "publishStatus": "published",
                "weight": 17,
                "items": [
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
                        "parents": [ ... ],
                        "slug": "preventie-1",
                        "properties": {
                            "type": "section"
                        }
                    }
                ],
                "parents": [ ... ],
                "slug": "dienstverlening-2",
                "properties": {
                    "type": "section"
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

Je zal merken dat de broodkruimel begint vanaf de root met dan het eerste element `dienstverlening` in de resourceList en in de items collectie ervan zit het kind `preventie`. 

Het gevraagde content item zit **niet** mee in de broodkruimel.
