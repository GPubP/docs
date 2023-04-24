# Content historiek
By default [haal je content op dat online](/wcmv4/content/content-item-read) is, i.e. het is gepubliceerd (lees hier meer over het [online concept](/common/content/content-life-cycle?id=online-vs-offline)) 

Wil je bijvoorbeeld de werkversie ophalen die een redacteur heeft bewaard na een eerdere publicatie, dan kan je dit via de **WCM Content Manager API**.
 
```shell
curl --location --request GET 'https://api-gw-a.antwerpen.be/acpaas/wcm-content-manager/v4/proxy/admin/content/v1/sites/<site-id>/content/<uuid>/history/<historyType>' \
--header 'apikey: <api-key>'
```

Je kan gebruik maken van de volgende `historyTypes`:

* `latest` - Hiermee haal je de laatste revisie op van dit content item, ongeacht de status (draft, published, …)
* `published` - hiermee haal je de laatste gepubliceerde revisie op van het content item
* `draft` - hiermee haal je de laatst bewaarde werkversie op van het content item
* `Opmerking` - eigengemaakte workflow statussen vallen hieronder.
* `pending_review` - hiermee haal je de laatste bewaarde revisie op van het content item met dat als status ‘klaar voor nakijken’
* `pending_publish` - hiermee haal je de laatste bewaarde revisie op van het content item met dat als status ‘klaar voor publicatie’
* `unpublished` - hiermee haal je de laatste bewaarde revisie op van het content item met dat als status ‘gearchiveerd’

