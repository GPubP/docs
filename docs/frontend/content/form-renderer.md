# Formulieren tonen

## Voorbereiding

Vooraleer je een formulier kan tonen loop je best deze stappenlijst door:

1. [Activeer de Forms module](/modules/content/modules/module-forms)
2. [Configureer de Forms Engine tenant](/redactie/content/inrichten-forms)
3. Maak een content type met een [Formulier referentie](/redactie/content/inrichten-cc-formulier-referentie)
4. Maak een content item en selecteer een formulier
5. [Haal het gekozen formulier op via de WCM API](/wcmv4/content/form-engine-integratie)

## Haal het formulier op

Het resultaat van de voorbereiding is dat je een `identifier` van het gekozen formulier bekomt. Deze laatste heb je nodig om het schema van het formulier op te halen.

Eerst moet je een geldig access token aanvragen:

```shell
curl --location --request POST 'https://api-gw.antwerpen.be/acpaas/form-survey-engine/v1/oauth2/authorize' \
--header 'apikey: <key>' \
--header 'Content-Type: application/json' \
--data-raw '{
  "client_id": <client_id>,
  "client_secret": <client_secret>,
  "response_type": "token",
  "scope": "",
  "provision_key": <provision_key>,
  "authenticated_userid": <authenticated_userid>
}'
```

Als reply krijg je het volgende, hier kan je de waarde van de access_token uitvissen.

```json
{
    "redirect_uri": "https://...auth/login/callback#access_token=alNt...56EPb&expires_in=7200&token_type=bearer"
}
```

Vervolgens kan je het schema van het formulier ophalen:

```shell
curl --location --request GET 'https://api-gw-a.antwerpen.be/acpaas/form-survey-engine/v1/forms/<identifier> \
--header 'dgp-tenant-id: <formsengine_tenant_uuid>' \
--header 'apikey: <api_key>' \
--header 'Authorization: Bearer <access_token>'
```

## De form renderer inbouwen in jouw frontend toepassing

> Zie [docs van de form renderer widget op bitbucket](https://bitbucket.antwerpen.be/projects/ACPFSE/repos/forms_engine_docs/browse/pages/widget.md).

Zet de [Form renderer](https://formwidget.antwerpen.be) op je frontend pagina.

* Hier is een [example implementatie](https://bitbucket.antwerpen.be/projects/AUI/repos/widgets_app_nodejs/browse/frontend/src/app/pages/examples/form-renderer-example/form-renderer-example.page.html?at=development-upco-84)
* Hier is een [demo](https://formwidget.antwerpen.be/demo/renderer)
* Hier is de [algemene info over widgets](https://widgets.antwerpen.be/welcome)
De widget verwacht het form schema en eventuele form data te krijgen.

## Bewaar een antwoord in de Forms Engine

Standaard gaat de renderer geen formulier data verwerken of doorsturen. Dit moet je zelf doen. Je zal het javascript event moeten opvangen en op basis hiervan de data naar de Forms Engine Response API sturen, je kan hier een voorbeeld implementatie ervan zien: <https://bitbucket.antwerpen.be/projects/SNA/repos/sna_proxy_nodejs/browse/src/server/modules/forms>
