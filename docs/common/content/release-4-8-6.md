# 4.8.5 Release notes

* **MTA**: 28 mei 2024
* **Release datum:** 18 juni 2024
* **Jira release:** Bekijk de [Jira release notes](https://jira.antwerpen.be/secure/ReleaseNote.jspa?projectId=14114&version=17090)
* **Getest door:** Axel Claeys, Erik Lenaerts
* **Release lead:** Jeroen Valcke
* **Product Owner:** Erik Lenaerts

## Algemeen

In deze release hebben we ons uitsluitend gefocussed op bugs. De MTO was een grote inhaalbeweging op vlak van onderliggende software componenten waardoor zowat alles in het systeem bijgewerkt is.
Dit heeft z'n gevolg gehad en tot heel best wat bugs geleid, sommige die pas later ontdekt zijn.
Daarnaast zijn we ook meer gebruik gaan maken van de navigatie v2 waardoor enkele kinderziektes naar boven gekomen zijn.

## Bug fixes

* **API**
  * **`Content beheerder`** Een standaard waarde instellen van een [custom content component](/redactie/content/inrichten-cc?id=samengestelde-of-custom-content-componenten) geeft geen fout meer.
  * **`Ontwikkelaar`** Wanneer de gevraagde site in API calls niet bestaat zal het systeem nu een HTTP 404 teruggeven.
  * **`Ontwikkelaar`** Wanneer een verkeerde apikey in API calls gebruikt wordt zal het systeem nu een HTTP 401 teruggeven.
  * **`Ontwikkelaar`** Wanneer een onbestaand content item wordt opgevraagd zal het systeem nu een HTTP 404 teruggeven in combinatie met de no-cache header.
  * **`Ontwikkelaar`** Het [published event](/redactie/content/inrichten-events) wordt nu gestuurd nadat de cache geïnvalideerd is.
  * **`Ontwikkelaar`** De [payload optimalisatie](/wcmv4/content/content-payload) werkt nu beter wanneer fields=false wordt gebruikt of specifieke meta filtering.

* **Content**
  * **`Redacteur`** Bug gefixed waarbij het content overzicht leeg bleef.
  * **`Redacteur`** Bij het invullen van een meerdere [tijdsloten](/redactie/content/inrichten-cc-tijdstip) verschijnen de titels opnieuw.
  * **`Redacteur`** Soms begon het scherm te flikkeren wanneer men het menu van de redactie gebruikte.
  * **`Redacteur`** Er werd een anderstalige link gelegd bij het kiezen van een [content referentie](/redactie/content/inrichten-cc-content-ref).
  * **`Redacteur`** Sorteeropties van [views](/redactie/content/inrichten-views) worden nu correct gebruikt in de voorbeeldweergave
  * **`Redacteur`** Onterechte melding over de slug is verdwenen voor content items met speciale karakters in de titel.
  * **`Redacteur`** Bug gefixed waarbij de lijst van tenants occasioneel leeg was.
  * **`Redacteur`** De 'wijzigingen bewaren' modal word niet meer getoond bij het bewaren van een [taxonomie term](/redactie/content/inrichten-taxonomie).
  * **`Redacteur`** De 'wijzigingen bewaren' modal word niet meer getoond bij het bewaren van een [view](/redactie/content/inrichten-views).
  * **`Content beheerder`** Je kan nu een default waarde instellen voor een [formulier referentie](/redactie/content/inrichten-cc-formulier-referentie).
  * **`Content beheerder`** [Meta](/redactie/content/inrichten-cc-meta) en [OG](/redactie/content/inrichten-cc-opengraph) werden niet voorzien in de OMG tenant bij aanmaken van een content type.
  * **`Content beheerder`** De waarde van keuzevakjes kunnen nu correct meegenomen worden wanneer men anderstalige content maakt.
  * **`Content beheerder`** Bug gefixed waarbij de sortering van de content componenten verkeerd stond bij het maken van een nieuw content type.

* **Navigatie v2**
  * **`Redacteur`** Bij het maken van een [tussentitel](/redactie/content/inrichten-navigatie-menu) op een menu komt deze niet meer dubbel voor.
  * **`Redacteur`** Een leeg [menu](/redactie/content/inrichten-navigatie-menu) toonde nog menu items van een menu waar je ervoor naar keek.
  * **`Redacteur`** [Sitestructuur items](/redactie/content/inrichten-navigatie-sitestructuur) worden nu correct geactiveerd bij publicatie van het bijhorende content item.
  * **`Redacteur`** Aanmaken van een [menu item](/redactie/content/inrichten-navigatie-menu) geeft geen WSOD meer.
  * **`Redacteur`** De 'wijzigingen bewaren' modal word niet meer getoond bij het bewaren van een [menu item](/redactie/content/inrichten-navigatie-menu) of [site structuur item](/redactie/content/inrichten-navigatie-sitestructuur).
  * **`Content beheerder`** [item:id] kan nu wel gebruikt worden in een [url patroon](/redactie/content/inrichten-content-types?id=url-patronen).
  * **`Content beheerder`** bug fix in de opbouw van een url waarbij er bv al een taal in de siteurl vast stond.
  * **`Ontwikkelaar`** externalUrl wordt nu correct opgevuld voor een [menu item](/redactie/content/inrichten-navigatie-menu) gelinkt aan een content item.
  
* **Search**
  * **`Content beheerder`** Het herindexeren blijft niet meer hangen op 0%.
  * **`Content beheerder`** De volgorde van de [content componenten in een search index](/redactie/content/inrichten-search-beheren?id=wat-wordt-er-ge%c3%afndexeerd) komen overeen met het content type.
  * **`Ontwikkelaar`** De [Zoekindex referentie component](/redactie/content/inrichten-cc-zoekindex-referentie) geeft nu ook de taal mee.

* **Systeem**
  * **`Redacteur`** Als gebruiker van een tenant kon ik onterecht de talen configureren van die tenant zonder de specifieke rechten ervoor te hebben.
  * **`Redacteur`** De rechten van een gebruiker worden nu beter afgehandeld ingeval er problemen waren met achterliggende systemen zoals BRaaS.
  * **`Tenant beheerder`** Enkele ontbrekende module dependencies zijn bijgewerkt.

?> Bekijk hier het overzicht van [alle releases](/RELEASE).
