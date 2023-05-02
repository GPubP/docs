# Taxonomiëen

## Read Taxonomie 
### Enkel de taxonomie basis informatie
```shell
GET '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}/settings'
```

In het pad geef je de `id` van de taxonomie die je wenst op te vragen

### Taxonomie basis informatie + de termen 

```shell
GET '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}'
```

In het pad geef je de `id` van de taxonomie die je wenst op te vragen

Bepaal hoeveel je wil ophalen via de optionele `page` en `pagesize` query parameters.

## Create taxonomie

```shell
POST '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies' \
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

Als payload geef je het volgende mee: 

```json
{
  "label": "Thema",
  "description": "Via de thema taxonomie bepalen we he...",
  "publishStatus": "published",
  "multiLanguage": true
}
```

Waarbij de `publishStatus` **draft** of **published** kan bevatten.

## Update taxonomie
```shell
POST '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}' \
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

In het pad geef je de `id` van de taxonomie die je wenst aan te passen.

Als payload geef je het volgende mee: 

```json
{
  "id": 67,
  "label": "Thema",
  "description": "Via de thema taxonomie bepalen we he...",
  "publishStatus": "draft",
  "multiLanguage": true
}
```

Waarbij de `publishStatus` **draft** of **published** kan bevatten.

## Delete taxonomie
```shell
DELETE '/wcm-content-manager/v4/proxy/admin/taxonomies/v1/taxonomies/{id}' \
```

In het pad geef je de `id` van de taxonomie die je wenst aan te verwijderen.