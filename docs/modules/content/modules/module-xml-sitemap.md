# XML-sitemap

Module om een XML-sitemap te exposen via API 

JIRA : [https://jira.antwerpen.be/browse/RED-3721](https://jira.antwerpen.be/browse/RED-3721)

## Inrichting redactie

#### Elastic App search

Het genereren van een xml-sitemap gebeurt op basis van records in Elastic. Je kan een index gebruiken die reeds is opgezet (om de zoek van je site te organiseren) maar je kan er ook voor kiezen om een volledig nieuwe index op te zetten. 

Voor de XML sitemap is het niet nodig om de volledige content items te indexeren, in principe is enkel de titel voldoende. 
De andere velden (i.e. last_modified datum)  worden automatisch aangemaakt in Elastic

Meer over de configuratie van Elastic vind je [hier](/redactie/content/inrichten-search-beheren)




#### WCM admin configuratie

Per tenant (toegang is enkel WCM Admins) kan de XML sitemap module geactiveerd worden. :

* ACC : https://wcm-admin-a.antwerpen.be/home
* PROD : https://wcm-admin.antwerpen.be/home



Na het activeren van de XML Sitemap module kan er in de XML Sitemap BSL configuratie per site toegevoegd worden via volgende JSON structuur :

```json
{
  "moduleConfig": {
    "sites": [
      {
        "uuid": "[site:id]",
        "indexName": "[elastic-engine-index zonder de language suffix]",
        "languages": [
          "[taal-suffix-1]",
          "[taal-suffix-2]",
          "[taal-suffix-3]",
          "..."
        "name": "[name]",
        "copyright": "[copyright]"
      },
      {
        "uuid": "[site:id]",
        "indexName": "[elastic-engine-index zonder de language suffix]",
        "languages": [
           "[taal-suffix-1]",
            "[taal-suffix-2]",
        ],
        "name": "[name]",
        "copyright": "[copyright]"
      }
    ]
  }
}
```

### API

Na het activeren van de XML Sitemap module en het configureren van de sitemap voor een site kan de Frontend applicatie referenties naar de XML Sitemaps als volgt ophalen :

```shell
GET /wcm-proxy/v4/xml-sitemap/v1/sites/[siteId]/sitemaps
```

Het resultaat is een lijst van verwijzingen naar gegenereerde sitemaps :

```json
{
    "_embedded": [
      /*  array van sitemaps per taal ... */
        {
            "meta": {
                "siteId": "[:siteId]",
                "tenantId": "[:tenantId]",
                "indexName": "[:elastic-engine-index zonder de language suffix]",
                "language": "[:language-suffix]",
                "modifiedAt": "2025-09-18T09:00:04.892Z",
                "createdAt": "2025-09-18T09:00:04.892Z"
            },
            "data": {
                "assetPath": "/assets/v1/sites/ebb357ad-889f-4d4b-81f5-57d5691ba815/assets/f12211a6-058a-4cad-b75a-5c140c91fe94/file",
                "assetId": "f12211a6-058a-4cad-b75a-5c140c91fe94",
                "file": {
                    "type": {
                        "mime": "application/xml",
                        "extension": "xml"
                    },
                    "size": 64181,
                    "reference": "823b10c7-f838-4ebd-ab76-83583d4d7738",
                    "name": "sitemap-ebb357ad-889f-4d4b-81f5-57d5691ba815-nl.xml"
                }
            },
            "uuid": "f12211a6-058a-4cad-b75a-5c140c91fe94"
        },
        {
          /* 
          "meta": {
            "siteId": "[:siteId]",
            "tenantId": "[:tenantId]",
            "indexName": "[:elastic-engine-inde
            "language": "[:language-suffix]",
            ....... 

          */  
        },
        
    ],
    "_page": {
        "size": 10,
        "totalElements": 5,
        "totalPages": 1,
        "number": 0
    },
    "_links": {}
}
```
Op basis van de uuid (of assetId) uit de bovenstaande call kan je de XML sitemaps zelf ophalen :

```shell
GET /wcm-proxy/v4/assets/v1/sites/[:siteId]/assets/[:assetId]/file
```
Het resultaat is een XML Sitemap file die voldoet aan de XML Sitemap standaard


## Nuttige links : 

* [Google search central](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap#general-guidelines|)
 * [Sitemap index](https://developers.google.com/search/docs/crawling-indexing/sitemaps/large-sitemaps)
