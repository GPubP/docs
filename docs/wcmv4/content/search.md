# Search API

De Search API is geen onderdeel van de WCM API. Veel zaken zoals taxonomy en navigatie zijn achterliggend andere subsystemen en de WCM API ontsluit deze voor de afnemers. 

!> Voor Search hebben we gekozen dat afnemers **rechtstreeks** de Search API aanspreken. 

Op deze manier kunnen afnemers maximale snelheid bekomen wat essentieel is in search scenario's zoals het produceren van suggestielijsten in een autocomplete veld. 

?> De Search API docs kan je hier terugvinden: https://www.elastic.co/guide/en/app-search/current/search.html

## Index keuze

Elke site kan één of meerdere search indexen bevatten. Dit wordt door de [Site beheerder hier ingericht](/redactie/content/inrichten-search). 

In veel gevallen zal de `index` die je zal gebruiken voor je zoekopdrachten uit de WCM komen. Hiervoor maken content beheerders vaak een specifiek [content type](/redactie/content/inrichten-content-types) dat ze **zoekpagina** of **lijstpagina** noemen. Hier voegen ze een [Zoekindex referentie](/redactie/content/inrichten-cc-zoekindex-referentie) waarmee de keuze van de index vastgelegd kan worden.  

