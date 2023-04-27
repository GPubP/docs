# Formulieren

Door gebruik te maken van een [formulier referentie](/redactie/content/inrichten-cc-formulier-referentie) content component kan je aan de redacteur een lijst aanbieden van formulieren waaruit hij/zij kan kiezen.

Lees [hier de info](/redactie/content/inrichten-forms), hoe je deze moet installeren en gebruiken voor een inrichting.

Haal via de WCM proxy API een content item op waarbij een redacteur een formulier gekozen heeft.
```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/content?slug={slug}&lang={lang}
```

Dan krijg je:

```json
{
    "_id": "60ed5a1b89af600009e20a10",
    ...
    "fields": {
        "formulier": {
             "identifier": "verloren-voorwerp-claimen"
        }
    },
    ...
    "uuid": "00f48cd6-ac58-4921-8eea-46c0f51f95ec"
}
```

Het is deze `identifier` dat je nodig hebt om het gekozen [formulier te tonen (aka renderen) in de frontend](/frontend/content/form-renderer).