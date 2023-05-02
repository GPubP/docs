# Content verwijderen

> [!WARNING|label:Opmerking]
> In plaats van content te **verwijderen**, is het dikwijls veel veiliger om content te **archiveren**. Er kunnen namelijk heel wat referenties liggen naar de content dat je wil weghalen. Door het te archiveren verbreek je deze relaties niet en is het content item toch onbeschikbaar.

## Content archiveren

Content archiveren kan je door de [status van het content item aan te passen](/wcmv4/content/content-write-update?id=status-verzetten).

## Content verwijderen

Content effectief verwijderen kan je via het `DELETE` commando. 

```shell
DELETE '/wcm-proxy/v4/wcm-content-manager/v4/proxy/admin/content/v1/sites/{id}/content/{uuid}' \
```
