# Formulier referentie
Met dit content component kunnen redacteurs formulieren kiezen die gemaakt zijn met de [Form Composer](https://formcomposer.antwerpen.be).

> Zorg ervoor de de [Forms module](/modules/content/modules/module-forms) geactiveerd is en dat deze [goed is geconfigureerd](/redactie/content/inrichten-forms).

## Voor contentbeheerders

Je kan een formulier referentie instellen zodat het als link kan gebruikt worden met een link opschrift. (Gelijkaardig als een [content referentie](/redactie/content/inrichten-cc-content-ref)). Daarnaast kan je aangeven of dit een verplicht veld is of niet.

![Formulier referentie config](../assets/formulier-referentie-config-2.jpg)

## Voor redacteurs

Redacteurs krijgen een autocomplete zoekveld waarin de lijst zit van alle formulieren die beschikbaar zijn in de geconfigureerde forms engine tenant.

![Formulier referentie config](../assets/formulier-referentie-config.png)

## Voor ontwikkelaars

De output van het formulier referentie veld is de `identifier` van het formulier dat de redacteur gekozen heeft. Deze identifier is een unieke nummer van het formulier uit de forms engine. 

```json
{
    "_id": "6206dc0c0c7666000935d857",
    "fields": {
        "formulier": {
            "identifier": "inschrijving activiteit"
        }
    },
    "uuid": "c787fecf-0d99-4c7c-b2c0-56c9a6ea1ace"
}
```

## Voor bezoekers
Bezoekers zien het formulier op een web pagina dat gerenderd wordt door de Form Renderer widget. [Hier kan je lezen](/frontend/content/form-renderer) hoe je het formulier kan renderen op je frontend.


?> Ga terug naar het [overzicht van alle content componenten](/redactie/content/inrichten-cc-standaard.md)