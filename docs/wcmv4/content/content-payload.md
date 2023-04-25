# Payload optimaliseren
Er zijn vele gevallen waarbij je een [content item](/wcmv4/content/content-item-read) ophaalt of een lijst (via een view) waarbij je slechts een klein deel nodig hebt. Hoe minder over de lijn gaat hoe sneller en beter voor de algemene performantie. Hieronder beschrijven we hoe je data en/of meta data kan filteren uit de resultaten.

We maken hieronder steeds gebruik van de [WCM Proxy endpoint](/wcmv4/content/endpoint-proxy).

## Data filteren
Door gebruik te maken van de `fields` query-parameter kan je aangeven waarin je geïnteresseerd bent. 

### Simpel voorbeeld:

Stel we hebben een kantoor content type, waarvan ik enkel de naam en de stad nodig heb. De stad is weliswaar onderdeel van een adres dat bestaat uit een straat, postcode en stad. 

*Haal content item hoofdkantoor op met enkel de naam en de stad (van het adres).*
```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/content?slug=hoofdkantoor&fields=naam,adres(stad)&lang=nl
```

Het adres is in dit voorbeeld geen content referentie, het is een custom component dat onderdeel is van het kantoor content type waardoor het in een extra field group resulteert. 

> Indien één van de velden niet bestaat wordt dit genegeerd.

### Uitgebreid voorbeeld:

Op een homepage staat er een call-to-action component. Dit bevat één of meerdere interne of externe linken. 

```shell
GET .../view?uuid=42bb...f40c&fields=call-to-action(link(value(content(titel(text)))))&populate=call-to-action.link&meta=false&lang=nl
```

Geeft als resultaat: 
```json
{
    "_id": "60b9f2a96729070009ad4a86",
    "fields": {
        "call-to-action": {
            "link": [
                {
                    "preset": "b2f2e787-9b3d-4857-97fd-abb597493b73",
                    "fieldType": "07d930ac-6094-45de-a53d-c57f4dd0fdb6",
                    "fieldRef": "0e80fa5c-9352-4e2c-883d-372d2c02837a",
                    "type": "fieldgroup",
                    "uuid": "d94808e0-5441-4bcd-b98f-c6c8c7e267c2",
                    "value": {
                        "text": "Schrijf je in",
                        "content": {
                            "_id": "60b740ef11264300093a9504",
                            "fields": {
                                "titel": {
                                    "text": "My first news item"
                                }
                            },
                            "uuid": "bb023067-5a57-46c7-ab07-e169f31b2533"
                        },
                        "style": "none",
                        "target": "_self"
                    },
                    "semanticType": "content-referentie",
                    "multiple": false
                }
            ]
        }
    }
}
```

laten we even inzoomen op de structuur van deze output:

`call-to-action` is een paragraaf systeem (zie ook Werken met paragrafen TODO: < linken) waarbij de redacteur kan kiezen tussen een interne link ([Content Referentie](/redactie/content/inrichten-cc-content-ref)) of een externe link ([Link](/redactie/content/inrichten-cc-link)). Er kunnen meerdere van deze voorkomen, vandaar dat de `Link` een JSON array is. 

Aan het `semanticType` zien we dat er hier een interne link (aka content referentie) is gelegd door de redacteur. 
Onder `value`, vinden we de gerefereerde content terug. Doordat we eveneens een populate parameter hebben meegegeven, wordt deze [content referentie gepopuleerd](/wcmv4/content/content-item-read-related). Het resultaat is dat er onder de content nu ook de `fields` verschijnt. `Meta` hebben we even uitgeschakeld (zie [hieronder](/wcmv4/content/content-payload?id=metadata-filteren))

Stel dat je enkel de titels wilt van alle call to actions dan gebruik je volgende filter:

```shell
...&fields=call-to-action(link(value(content(titel(text)))))
```

In essentie kan je deze zelf samenstellen door de payload hiërarchie af te lopen. 

> [!info|label:Opmerking]
> Merk op dat je fields nooit moet mee gebruiken in deze filter syntax. In het voorbeeld hierboven schrijf je dus:
> ```shell
> ...&fields=call-to-action(link(value(content(titel(text)))))
> ```
> in plaats van
> ```shell
> ...&fields=call-to-action(link(value(content(fields(titel(text))))))
> ```

## Metadata filteren
Op een gelijkaardige manier kan je metadata filteren door gebruik te maken van de `meta` query-parameter.

*Haal content item hoofdkantoor op met enkel de site en de slug uit de meta data.*
```shell
GET .../content?slug=hoofdkantoor&lang=nl&meta=site,slug(nl)  
```

Als je **enkel de metadata** wil ophalen, kan je gebruik maken van `fields=false` query-parameter. 

*Haal enkel de meta data op van content item hoofdkantoor.*
```shell
GET .../content?slug=hoofdkantoor&lang=nl&fields=false
```

Je kan dit combineren met het ophalen van slechts **enkele delen uit de metadata**.

*Haal enkel de site en de slug op van de meta data op van content item hoofdkantoor.*
```shell
GET .../content?slug=hoofdkantoor&lang=nl&fields=false&meta=site,slug(nl)
```

Je kan ook kiezen om **geen metadata** op te halen met de `meta=false` query-parameter.

*Haal enkel de data op van content item hoofdkantoor.*
```shell
GET .../content?slug=hoofdkantoor&lang=nl&meta=false
```

Je kan bovenstaande technieken combineren en zo precies bepalen welke **gerelateerde data** je wil ophalen.

*Haal content item regio-noord op, maar enkel de naam en de stad van het gelinkte kantoor, zonder metadata.*
```shell
GET .../content?slug=regio-noord&populate=kantoor&fields=kantoor(naam,adres(stad))&meta=false&lang=nl 
```

*Haal content item regio-noord op, maar enkel de naam en de stad van het gelinkte kantoor. Voor het gelinkte kantoor willen we ook enkel de datum van creatie metadata.*
```shell
GET .../content?slug=regio-noord&populate=kantoor&fields=kantoor(naam,adres(stad))&meta=kantoor(created)&lang=nl 
```

