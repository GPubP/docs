# Logbook module

> [!info|label:Definitie]
> Met deze module kan je logs sturen naar een gecentraliseerde log in de WCM. De logs zijn rechtrstreeks beschikbaar en doorzoekbaar in de WCM.

## Logs versturen
De essentie van deze module is om logs te centraliseren per site en tenant. Als [Content beheerder](/redactie/content/toegang-content-beheerder) kan je deze logs raadplegen en doorzoeken. Ga hiervoor naar de tenant of site naar keuze en selecteer `logboek`.

![Logbook module concept](.//modules/assets/wcm-logbook-module-1.png 'Menu van de logbook module.')

## Implementatie

Door gebruik te maken van de `requestModule` functie van `tenantConfig` kan de logbook module aangesproken worden door andere WCM modules. De logbook module verwacht een body met volgende parameters: 

```
{
  "title": "Logging entry title",
  "date": "yyyy-MM-ddTHH:mm:ssZ",
  "content": "Log content"
}
```

De `date` parameter verwacht een UTC formaat. De `Title` en de `content` zijn beide Strings. 

Voor het schrijven naar de logbook module voor een site kan de volgende implementatie gebruikt worden:

```
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

```
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

Waarbij tenantKey opgehaald kan worden via: 

```
static getTenantKey(tenantApikey: string): string {
    const allApps = tenantConfig.getAllApps();
    return allApps.find((app: any) => app.uuid === tenantApikey)?.apikey;
}
```

?> Ga terug naar het [overzicht van alle modules](/modules/content/wcm-modules)
