# Previews

Soms willen Redacteurs hun voorlopig werk kunnen bekijken op de frontend.
Deze ondersetuning moet ingebouwd worden in de frontend zoals je hieronder kan lezen.

## Voorbereidingen

1. De [Preview module](/modules/content/modules/module-preview) moet geactiveerd zijn voor jouw tenant.
2. De preview moet [ingericht zijn in de Redactie](/redactie/content/inrichten-preview).

## Preview url

Een preview werkt met een specifieke url, bv <https://www.mijnsite.be/preview/slugxyz?wcm-preview-id=40d0110c-4172-4174-9a33-8be2b06952fa>.

Deze url bestaat uit 3 delen:

1. de root van de preview url; <https://www.mijnsite.be/preview/>. Dit wordt in de Redactie ingericht.
Deze zou je kunnen gebruiken in de frontend om te herkennen dat het over een preview gaat.
2. de slug van de pagina die men wil previewen.
3. het `preview token` in de query parameter

Belangrijk is dat deze url:

* de url kan gedeeld worden met andere mensen zodat ze mee kunnen zien wat er gaat komen
* de url blijft `24h` geldig.
* de preview url toont steeds de laatste stand van zaken, ook al zijn er wijzigingen gemaakt nadat deze link werd uitgegeven

## Preview content ophalen

Via de [content API](/wcmv4/content/content) ben je gewoon om content op te halen dat gepubliceerd is.
Door de preview token zal je dus ook content kunnen ophalen dat nog niet gepubliceerd is.

Dit doe je als volgt, gebruik je call om content op te halen via een slug en voeg daarbij de `preview` param aan toe met het token dat je in de preview url kreeg.

```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/content?slug={slug}&lang={lang}&preview={token}
```

?> Meer info hierover kan je vinden in de [Content API](/wcmv4/content/content-item-read?id=preview-content).

## UX

Om redacteurs op de hoogte te brengen dat ze een preview aan't bekijken zijn is het best dat je dit visueel duidelijk maakt voor hen.
Dit kan door een extra banner of aanduideing te brengen zoals dit:

![Preview banner](../assets/frontend-dev-preview-banner.jpg 'Een extra aanduiding zodat redacteurs bewust zijn dat ze een preview aan het bekijken zijn.')
