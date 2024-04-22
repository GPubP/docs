# Release notes [4.8.5]: 2024-04-30

Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=16908)

## Nieuwe features

* **Content**
  * **`Redacteur`** De [GIS kaart](/redactie/content/inrichten-cc-gis-kaart) werkt nu op basis van de meest recente kaart van Antwerpen.
  * **`Ontwikkelaar`** Extra documentatie voor het werken met de nieuwe [GIS kaart](/redactie/content/inrichten-cc-gis-kaart).
  * **`Ontwikkelaar`** De JSON GIS data van de [GIS kaart](/redactie/content/inrichten-cc-gis-kaart) is bijgewerkt zodat alles een consistente plaats heeft.

* **Privacy**
  * **`Redacteur`** De persoonsgegevens van een redacteur worden gewist van zodra gearchiveerde content ouder is 1 jaar. Nadien zie je *'Naam auteur gewist (GDPR)'*.
  * **`Tenant beheerder`** Je kan zien wie wanneer aan - en afmeld, ook wanneer iemand werkt met een specifieke tenant. (Deze log entries worden voorzien door de Audit module).
* **Search**
  * **`Redacteur`** Je kan per content item aangeven of deze opgenomen moet worden in een Elastic App Search index of niet.
  * **`Redacteur`** Je kan per content item zien wanneer deze laatst geïndexeerd is per index
  * **`Redacteur`** Je kan elk content item apart herindexeren
  * **`Redacteur`** Je kan elk content item apart uit een index verwijderen
  * **`Ontwikkelaar`** [Extra documentatie en componenten](/modules/content/developer-guides/search-helper/index) die het maken van een Search Mapper vereenvoudigen voor andere contributors.
  * **`Content beheerder`** Via de [Open Graph teaser mapper](/redactie/content/inrichten-search-beheren?id=search-mappers) kan [Open Graph](/redactie/content/inrichten-cc-opengraph) description overgezet worden naar de Summary in de Elastic App Search Engine
  * **`Content beheerder`** Content blokken kunnen nu mee opgenomen worden in Elastic App Search. De url van deze geïndexeerder content blokken kan ingesteld worden in de Index configuratie
  * **`Content beheerder`** Er is een extra [Hoofdafbeelding](/redactie/content/inrichten-search-beheren?id=search-mappers) search mapper om aan te geven welk content component de afbeelding zal leveren in de Index.

## Veranderingen

* **Algemeen**
  * **`Redacteur`** De boodschap op het portaal om toegang aan te vragen is bijgewerkt. Verwijzingen naar UM zijn verdwenen.

## Bug fixes

* **API**
  * **`Ontwikkelaar`** Bij het ophalen van content worden referenties opnieuw gepopuleerd.
  * **`Ontwikkelaar`** Content met dezelfde slug over talen heen is gefixed.
  
* **Content**
  * **`Redacteur`** De bewaar knoppen worden terug grijs nadat je als redacteur iets bewaard hebt.
  * **`Redacteur`** Gepland publiceren is terug hersteld
  * **`Support`** Voor push notificaties ikv de Mijn Antwerpen App, worden nu terug events verstuurd voor push notificaties
  
* **Search**
  * **`Support`** Het systeem zal niet meer vastlopen wanneer teveel rubrieken worden toegevoegd aan een paragraaf.
  * **`Content beheerder`** De rechten van de Search module worden nu correct afgedwongen.

* **Site**
  * **`Content beheerder`** De `site:url` pattern was onnodig en is verwijderd.

* **System**
  * **`Support`** Firewall regels bijgewerkt ten gevolge van de Move To Orange.

?> Bekijk hier het overzicht van [alle releases](/RELEASE).
