# Content ophalen voor view referenties
Ingeval je een view referentie wil **populeren**, gaat de lijst van content worden opgenomen in de payload van het content item dat je gaat opvragen.

Laten we dit verduidelijken. Er is een content item met een referentie `snelheidscontroles` welke verwijst naar een view (i.e. view referentie).

```json
 {
    "_id": "60b9f2a96729070009ad4a86",
    "fields": {
        ...
        "snelheidscontroles": "6014680d-845c-4287-bd94-8c15a2bf5e06"
        ...
    },
    "uuid": "215cbad9-2fec-4bc4-9461-4197153aabf5",
    ...
}
```

Willen we in één call het content item ophalen inclusief de lijst van snelheidscontroles, dan gebruiken we de [populatie parameter](/wcmv4/content/content-item-read-related).

*Haal content item home-page op, inclusief de lijst van snelheidscontroles*
```shell
GET .../content?slug=home-page&lang=nl&populate=snelheidscontroles 
```

Dit resulteert in het volgende:

```json
{
    "_id": "60b9f2a96729070009ad4a86",
    "fields": {
        ...
        "snelheidscontroles": {
           "_links": {
              "self": { "href": ".../sites/8fd9f2f1-2b61-41ff-81fe-4240e5890390/views?uuid42bb..." },
              "first": { "href": ".../sites/8fd9f2...e5890390/views?uuid42bb...&page=1&pagesize=10" },
              "last": { "href": ".../sites/8fd9f2...e5890390/views?uuid42bb…&page=2&pagesize=10" }
           },
           "_embedded": [
	         ...
           ],
           "_page": {
              "size": 10,
              "totalElements": 12,
              "totalPages": 2,
              "number": 1
           }
        }
        ...
    },
    "uuid": "215cbad9-2fec-4bc4-9461-4197153aabf5",
    ...
}
```

Zoals je kan zien is de lijst van snelheidscontroles gevuld. De inhoud is identiek aan de inhoud alsof je de view rechtstreeks zou opgevraagd hebben.

Het voordeel van de `_links` sectie is dat je meteen enkele linken krijgt waarmee je de call kan uitvoeren naar volgende pagina’s. Het `_embedded` gedeelte bevat meteen de data en de `_page` geeft info over de pages en de positie. 

### Welke page en pagesize wordt er gehanteerd?
Als je een lijst ophaalt via een [view call](/wcmv4/content/content-views-read) geef je een `page` en `pagesize` query-parameter mee, zo kan je de paging sturen van deze lijst. Vermits je in deze use case een content item ophaalt waar je een view referentie populeert, kan je in dit geval deze page en pagesize parameters niet meegeven. Vooral als je meerdere view referenties zou populeren, dan heb je geen idee op wat deze page en pagesize parameters slagen. 

Vandaar dat de WCM in geval van een populatie van een view referentie, de page en pagesize instellingen neemt die geconfigureerd staan in de redactie (door de inrichter). Wil je met andere woorden meer content items terug krijgen dan ga je in de redactie de [configuratie](/redactie/content/inrichten-views) van deze view moeten aanpassen.
