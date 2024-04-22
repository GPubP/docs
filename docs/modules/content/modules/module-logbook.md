# Logbook module

> [!info|label:Definitie]
> Met deze module kan je logs sturen naar een gecentraliseerde log in de WCM. De logs zijn rechtrstreeks beschikbaar en doorzoekbaar in de WCM.

## Logs raadplegen

De essentie van deze module is om logs te centraliseren per site en tenant zodat [Content beheerders](/redactie/content/toegang-content-beheerder) of [Site beheerders](/redactie/content/toegang-site-beheerder) een eerste idee kunnen vormen van de gebeurtenissen in het systeem.
Hiermee kunnen ze een indicatie krijgen ingeval van problemen.
Voor uitgebreide logging is het wel noodzakelijk om de technische logs erbij te nemen.

Ga hiervoor naar de tenant of site naar keuze en selecteer `logboek`.

![Logbook module concept](.//modules/assets/logbook-module-1.png 'Menu van de logbook module.')

Merk op dat het logbook beschikbaar is zowel op [tenant](/common/content/concept-tenant) als op [site](/common/content/concept-site) niveau. Bij deze laatste kan je enkel de logs van de site zelf bekijken.

## Log entries

Elk log entry bevat informatie over:

* Het tijdstip
* De site
* Een type (TODO)
* Een omschrijving
* De module van waar de entry komt zoals bv. de `Audit` module.  

## Zoeken in het logbook

!> todo

## Hoe gebruik ik als ontwikkelaar het logbook

Door gebruik te maken van de `requestModule` functie van `tenantConfig` kan de logbook module aangesproken worden door andere WCM modules. De logbook module verwacht een body met volgende parameters:

```json
{
  "title": "Logging entry title",
  "date": "yyyy-MM-ddTHH:mm:ssZ",
  "content": "Log content",
  "source": "Log source"
}
```

De `date` parameter verwacht een UTC formaat. De `Title`, `content` en `source` zijn Strings.

Voor het schrijven naar de logbook module voor een site kan de volgende implementatie gebruikt worden:

```javascript
await tenantConfig.requestModule(
    tenantKey,
    'logbook',
    'POST',
    `v1/sites/${site}/logbook-items`,
    {
        json: loggingContent,
    }
)
```

Voor het schrijven naar de logbook module voor een tenant kan de volgende implementatie gebruikt worden:

```javascript
await tenantConfig.requestModule(
    tenantKey,
    'logbook',
    'POST',
    `v1/logbook-items`,
    {
        json: loggingContent,
    }
)
```

Waarbij `tenantKey` opgehaald kan worden via:

```javascript
static getTenantKey(tenantApikey: string): string {
    const allApps = tenantConfig.getAllApps();
    return allApps.find((app: any) => app.uuid === tenantApikey)?.apikey;
}
```

?> Ga terug naar het [overzicht van alle modules](/modules/content/wcm-modules)
