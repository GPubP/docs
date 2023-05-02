# Content historiek
By default [haal je content op dat online](/wcmv4/content/content-item-read) is oftwel gepubliceerde content. Wil je toch een werkversie ophalen die een redacteur heeft bewaard na een eerdere publicatie, dan kan je dit via onderstaande call doen. 

!> Merk dat je hier gebruik moet maken van het [WCM Content Manager endpoint](/wcmv4/content/endpoint-content-manager).
 
```shell
GET '/wcm-content-manager/v4/proxy/admin/content/v1/sites/{sId}/content/{uuid}/history/{historyType}' \
```

Je kan gebruik maken van de volgende `historyTypes`:

* `latest` - Hiermee haal je de laatste revisie op van dit content item, ongeacht de status (draft, published, …)
* `published` - hiermee haal je de laatste gepubliceerde revisie op van het content item
* `draft` - hiermee haal je de laatst bewaarde werkversie op van het content item
* `Opmerking` - eigengemaakte workflow statussen vallen hieronder.
* `pending_review` - hiermee haal je de laatste bewaarde revisie op van het content item met dat als status ‘klaar voor nakijken’
* `pending_publish` - hiermee haal je de laatste bewaarde revisie op van het content item met dat als status ‘klaar voor publicatie’
* `unpublished` - hiermee haal je de laatste bewaarde revisie op van het content item met dat als status ‘gearchiveerd’

?> lees meer over het [online/offline concept](/common/content/content-life-cycle?id=online-vs-offline)

