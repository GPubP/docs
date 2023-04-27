# Navigatie

Eerst en vooral willen we benadrukken dat het werken met navigatie gerelateerde zaken zoals broodkruimels, site structuren en menu’s **via de WCM API’s moet lopen**. Achterliggend werkt de WCM met de Navigation engine maar voegt daarbovenop nog enkele features aan toe die je gaat missen als je rechtstreeks met deze engine zou werken.

## Wat is navigatie
Met navigatie bedoelen we: 

* [Site structuur](/wcmv4/content/navigation-sitestructure): Redacteurs maken content items en ‘hangen’ deze in een boomstructuur. Frontends kunnen hiermee aan de bezoeker een pagina tonen met daaronder nog onderliggende pagina’s, zeg maar kinderen met meer detail. Er is maar één site structuur per site per taal.
* [broodkruimels](/wcmv4/content/navigation-breadcrumb): Wanneer je een pagina neemt, dieper in de boomstructuur wil je aan de frontend dikwijls een kruimelpad aanbieden zodat ze de hiërarchie van de pagina’s kunnen zien en kunnen doorklikken op de segmenten van deze broodkruimel om zo terug naar hoger gelegen pagina’s te navigeren.
* [menu’s](/wcmv4/content/navigation-menu): Een verzameling van linken naar content die soms bovenaan een site staat met hoofdonderwerpen. Een menu kan ook hiërarchisch ingericht zijn maar hoeft de site structuur helemaal niet te volgen. je kan bv ook een menu gemaakt worden voor de footer van een site. 
* [linken](/wcmv4/content/content-url-path): Elke pagina zelf heeft z’n eigen URL pad. Soms leggen redacteurs linken aan tussen pagina’s (door middel van content referenties) zodat bezoekers deze linken kunnen gebruiken om naar andere gerelateerde pagina’s te navigeren.
