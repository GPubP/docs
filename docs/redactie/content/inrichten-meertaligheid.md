# Meertaligheid inrichten

Sommige afnemers willen content in meerdere talen aanbieden aan hun gebruikers. Hierbij denken we aan: 

* Een afnemer kan content in een specifieke taal opvragen via de [WCM API](/wcmv4/README)
* Een afnemer kan éénvoudig vanuit één [content item](/common/content/concept-ci) overgaan naar datzelfde content item andere taal 
* Redacteurs kunnen gemakkelijk veranderen van taal voor één content item
* Het systeem kent vertaalbare en niet vertaalbare componenten zoals éénzelfde afbeelding over de talen heen
* Het systeem kan overweg met vertalingen van [taxonomieën](/redactie/content/inrichten-taxonomie)

## Talen instellen per tenant
Vooraleer je kan bepalen welke talen er gebruikt gaan wordt per site, moet je - als [tenant beheerder](/redactie/content/toegang-tenant-beheerder) - eerst de beschikbare talen op tenant niveau aangeven. 

1. Ga hiervoor naar je tenant
2. Kies `Talen` in het menu
3. Voeg de talen toe die je wenst ter beschikking te stellen voor de sites.

> Het systeem maakt achterliggend gebruik van [ISO 3166-1](https://nl.wikipedia.org/wiki/ISO_3166-1) taalcodes.


## Talen instellen per site

Voor elke site kan een [site beheerder](/redactie/content/toegang-site-beheerder) aangeven welke talen er gebruikt mogen worden. Hier kan gekozen worden uit de talen die voorzien zijn bij de tenant.

1. Ga hiervoor naar de instellingen van de site
2. activeer/deactiveer de talen die je wenst

**Tip:** Op het instellingen scherm van de site kan je opvolgen hoeveel content items er aanwezig zijn per taal.

## Content vertalen

Zie het luik [vertalen](/redactie/content/content-beheren-vertalen) onder content beheer.

## Taxonomie vertalen

Zie het luik [taxonomie](/redactie/content/content-beheren-taxonomie) onder content beheer.

## Content items in de WCM 

!> Todo: dit stuk nog verplaatsen naar het WCM hoofdstuk

Als redacteur kan je een [content item](/common/content/concept-ci) invoeren in een specifieke taal en kan je hiervan een vertaling maken. In de praktijk komt het erop neer dat het systeem meerdere content items aanmaakt en aan elkaar linkt door middel van één en dezelfde `translationId`.

>[!NOTE|icon:fas fa-info-circle|label:translationId]
>Elk content item representeert de content slechts in één taal. Content items die elkaars vertaling zijn delen hetzelfde `translationId`.
>``` plantuml
@startuml
object "content item NL" as contentItemNL {
 meta.lang:"nl"
 meta.slug:"plan-je-bezoek"
 meta.translationId: "c266aa05-...cc8199" 
}
object "content item FR" as contentItemFR {
 meta.lang:"fr"
 meta.slug:"planifier-votre-visite"
 meta.translationId: "c266aa05-...cc8199"
}
object "content item EN" as contentItemEN {
 meta.lang:"en"
 meta.slug:"plan-your-visit"
 meta.translationId: "c266aa05-...cc8199"
}
contentItemNL::meta.translationId <--> contentItemFR::meta.translationId
contentItemFR::meta.translationId <--> contentItemEN::meta.translationId
contentItemNL::meta.translationId <--> contentItemEN::meta.translationId
@enduml
>```

