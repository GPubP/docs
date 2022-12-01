# Formulier referentie
Met dit content component kunnen redacteurs formulieren kiezen die gemaakt zijn met de [Form Composer](https://formcomposer.antwerpen.be).

# Voorbereiding forms engine
De WCMv4 moet toegang krijgen tot jouw tenant op de Forms Engine. De WCM is gekend als de **Redactie WCM Forms** app. Dit doe je door een ticket aan support@digipolispoc.zendesk.com te richten met:

> [!info|label:Aanvraag]
>
> Beste
>
> kan de App **Redactie WCM Forms** voorzien worden op de tenant **&lt;tenant naam&gt;** (uuid=&lt;tenant uuid&gt;) op **ACC|Prod** ?
>
> dankjewel

# Voorbereiding redactie

> [!Warning|label:Module]
>
> Form referentie werkt enkel wanneer de Form BSL en Form module geactiveerd zijn voor deze tenant.

> [!Warning|label:Opmerking]
>
> Vergis je niet met de Form renderer module, deze wordt intern gebruikt door de redactie voor de opbouw van de content invoerschermen.

In de Form BSL kan je de Forms tenant configureren voor jouw WCMv4/Redactie tenant dmv de volgende configuratie: 

```json
{
  "dgpTenantId": "f5b61753-4295-4c10-b704-8540f80a192b"
}
```

# Voor contentbeheerders

Er zijn geen configuratie opties voor een Form Referentie veld.

# Voor redacteurs

Redacteurs krijgen een autocomplete zoekveld waarin de lijst zit van alle formulieren die beschikbaar zijn in de geconfigureerde forms engine tenant.

![Formulier referentie config](../assets/formulier-referentie-config.png)

# Voor ontwikkelaars

De output van het formulier referentie is een identifier veld. 

Bekijk de WCMv4 Content API gids, hier kan je [meer terugvinden](https://docs.google.com/document/d/1cMGpDkgqBnVhzlr7nr00YK8xciIESvIX1YmffqT6VzE/edit#heading=h.5tnr7bp3or0v) hoe je aan de slag gaat met Formulieren en de WCMv4.

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

# Voor bezoekers
Bezoekers zien het formulier op een web pagina dat gerenderd wordt door de Form Renderer widget. Hier is een [voorbeeld/demo](https://widgets.antwerpen.be/examples/form-renderer).


?> Ga terug naar het [overzicht van alle content componenten](/redactie/content/inrichten-cc-standaard.md)