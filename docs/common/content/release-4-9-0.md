# 4.9.0 Release notes

* **MTA**: september 2024
* **Release datum:** jan 2025
* **Jira release:** Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=15731)
* **Getest door:** Axel Claeys, Erik Lenaerts
* **Release lead:** Jeroen Valcke
* **Product Owner:** Erik Lenaerts

## Nieuwe features

* **API**
  * **`Ontwikkelaar`** Er is een `content-within-this-view-updated` [event waarop je kan werken](/frontend/content/events-consumeren).
  * **`Ontwikkelaar`** Er is een `search.content.index.upsert` en een `search.content.index.removed` event bijgekomen.

* **Content**
  * **`Redacteur`** Je kan aangeven om, linken naar een andere pagina vanuit een [tekstvak met opmaak](/redactie/content/inrichten-cc-tekstvak-met-opmaak), te laten openen in een nieuw tabblad/venster. *Merk op dat de afnemer dit wel moet ondersteunen.*
  * **`Redacteur`** Er is een vernieuwd en [uitgebreid overzicht van content items](/redactie/content/content-beheren-schrijven?id=content-bekijken).
  * **`Redacteur`** Het systeem herkent automatisch e-mail adressen als je deze plakt in een tekstvak met opmaak als link.
  * **`Redacteur`** Je kan content items dupliceren.
  * **`Redacteur`** Het scherm waarin je de meta data van een afbeelding aanpast is geöptimaliseerd.
  * **`Redacteur`** Linken in een tekstvak met opmaak worden automatisch bijgwerkt wanneer het content item wijzigt waarnaar ze verwijzen.
  * **`Redacteur`** Er zijn nieuwe opties beschikbaar voor het tekstvak met opmaak.
  * **`Redacteur`** Je kan taxonomieën nu makkelijker en overzichtelijker selecteren.
  * **`Content beheerder`** Je kan de volgorde bepalen van een content component in een [Paragraaf](/redactie/content/inrichten-cc-paragraaf).
  * **`Content beheerder`** Als beheerder kan ik een standaardwaarde voorzien voor een component in een custom content component.
  * **`Content beheerder`** Als beheerder kan ik per site een standaardwaarde voorzien voor een component.

* **Formulieren**
  * **`Redacteur`** Je kan informatie opvragen van een formulier dat je hebt gekozen via de [formulier referentie component](/redactie/content/inrichten-cc-formulier-referentie).

* **Logboek**
  * **`Content beheerder`** verschillende verbetering zijn toegevoegd aan het logbook, waaronder meer details dat je kan openen/sluiten per log entry. 
  * **`Content beheerder`** De inhoud van een log entry kan actieve linken bevatten naar bv content types, indexen, etc.
  * **`Content beheerder`** Er is ook een type aanduiding dat ofwel Info, Warning, Success, Error kan bevatten.

* **Navigatie v2**
  * **`Redacteur`** Als redacteur kan ik aangeven om een content item niet op te nemen in de sitestructuur.
  * **`Redacteur`** Als redacteur kan ik kiezen in welke sitestructuur ik m'n content item hang (indien er meerdere geconfigureerd zijn). 
  * **`Content beheerder`** Er kunnen meerdere site structuren gemaakt worden per site. Dit laat toe om complexe omgeving (zoals antwerpen.be) te voorzien van meerdere site structuren. Zo kan een aparte sistestructuur voorzien worden per district en zorgt dit voor beperktere broodkruimels. 
  * **`Content beheerder`** Er kan per content type bepaald worden welke sitestructuren er gekozen mogen worden door de redacteur.

* **Search**
  * **`Redacteur`** Als redacteur kan ik een herindexering doen [in functie van de tijd](/redactie/content/inrichten-search-beheren?id=herindexeren).
  * **`Content beheerder`** In het logboek kan je [search operaties veel gedetailleerder opvolgen](/redactie/content/inrichten-search-beheren) wanneer een bulk/batch indexatie is aangevraagd, gestart, beëindigd of onderbroken.
  * **`Content beheerder`** Je kan een [Content Referentie nu laten indexeren](/redactie/content/inrichten-search-beheren) inclusief z'n url.
  * **`Content beheerder`** Je kan een [Content Referentie nu laten indexeren](/redactie/content/inrichten-search-beheren) met de volledige inhoud van het content item waarnaar verwezen wordt.
  * **`Content beheerder`** Er is een aparte log van Search indexering acties (bij de EAS module).
  * **`Content beheerder`** Individuele componenten kunnen nu [gemapped worden](/redactie/content/inrichten-search-beheren) bij de configuratie van een Search index.

* **Systeem**
  * **`Content beheerder`** Bulk operaties (zoals herindexer) kunnen ge-offload worden zodat ze geen invloed hebben op het leveren van content.
  
## Veranderingen

* **Content**
  * **`Content beheerder`** De CKEditor is geüpgraded van het [Tekstvak met opmaak](/redactie/content/inrichten-cc-tekstvak-met-opmaak) content component.
  * **`Content beheerder`** Een veld van verborgen naar zichtbaar zetten gaat nu zonder issues.
  
* **Search**
  * **`Content beheerder`** De performantie van het herindexeren is geöptimaliseerd.

## Bug fixes

* **API**
  * **`Ontwikkelaar`** foutieve field parameters bij het ophalen van een content item of werken met een view, geven geen onverwachte resultaten meer terug.

* **Content**
  * **`Redacteur`** Probleem gefixed met vorige en volgende knoppen van de [kenburs/focus afbeelding uitbreidingen](/redactie/content/inrichten-cc-afbeelding?id=extra-configuratie).µ
  * **`Redacteur`** Plakken van linken in een [Video Referentie](/redactie/content/inrichten-cc-view-referentie) normaliseert nu steed naar de correcte YouTube url.

* **Navgatie v2**
  * **`Redacteur`** gepubliceerde content items worden nu ook actief in de sitestructuur waar ze voorkomen.
  * **`Redacteur`** Menu instellingen op het content item worden nu correct weergegeven en er is geen browser refresh meer nodig.

* **Search**
  * **`Content beheerder`** [Zoekindex veldreferentie](/redactie/content/inrichten-cc-zoekindex-veld-referentie) werkt terug.

* **Systeem**
  * **`Redacteur`** Wanneer je als gebruiker aanmeld terwijl het achterliggende authorisatie systeem er uit ligt dan verdwijnen nu je rechten niet meer die we gecached hebben.

?> Bekijk hier het overzicht van [alle releases](/RELEASE).
