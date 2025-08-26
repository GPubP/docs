# Sitestructuren inrichten

## Tenant niveau 

Bij het bewerken van een site (enkel beschikbaar voor de tenantbeheerder rol) kan je onder de tab Navigatie instellen of sitestructuren toegelaten zijn. Het activeren gaat één sitestructuur (per geactiveerde taal) aanmaken binnen je site. Op site niveau is het mogelijk om extra sitestructuren toe te voegen indien nodig.

![Sitestructuren activeren voor een site](../assets/navigatie-tenant-configuratie.png 'Sitestructuren activeren voor een site')


## Site niveau

### Overzicht sitestructuren

Menu : Structuur > Sitestructuren

Op deze pagina vind je de geactiveerde sitestructuren voor je site. Je kan extra sitestructuren aanmaken indien gewenst. (Veelal is dit echter niet nodig)

![Sitestructuren](../assets/navigatie-sitestructuren.png 'Sitestructuren overzicht')


### Content type

Menu : Structuur > content types

Op content type level kan je bepalen of, waar en in welke sitestructuur een content item van dat type kan hangen. Indien er meerdere sitestructuren zijn is het mogelijk om meerdere sitestructuren te activeren voor een content type. De redacteur kan dan kiezen in welke sitestructuur het content item hangt. 


![Content type : Sitestructuren](../assets/navigatie-ct-sitestructuur.png 'Content type : Sitestructuren')



### Per site structuur heb je volgende opties :

**Geen**
* Content items van dit type kunnen niet in de sitestructuur gehangen worden

**Beperkt**

* Je kan een standaard positie instellen. Dit zal de default 'parent' van het content item worden, een redacteur kan enkel content items onder die positie plaatsen 
* Je kan bepalen of de redacteur dit kan aanpassen. Indien je dit afvinkt kan de redacteur geen aanpassingen doen en zal het content item steeds onder de ingestelde standaard positie terecht komen

![Content type : Sitestructuren](../assets/navigatie-ct-sitestructuur-config.png 'Content type : Sitestructuren')


**Vrij**

* Je kan een standaard positie instellen. Dit zal de default 'parent' van het content item worden maar een redacteur kan content items onder een volledig andere positie plaatsen.

### Content niveau
Vanuit het content item zelf kan je slechts één keer een plaats kiezen. Dit is de ‘primaire plaats’ die (meestal) de broodkruimel gaat bepalen

### Rechten

De navigatie module voorziet volgende rechten voor het beheer van sitestructuren (meer over [rollen en rechten](/redactie/content/toegang-rollen-rechten).)

**Sitestructuur**

* **Sitestructure read** : geeft toegang tot het overzicht van  sitestructuren
* **Sitestructure create** : geeft recht om nieuwe sitestructuren aan te maken
* **Sitestructure update** : geeft recht om de sitestructuur te bewerken

**Sitestructuur item**

* **Sitestructure items read** : geeft toegang tot het sitestructuur compartiment
* **Sitestructure items create** : geeft het recht content items in de sitestructuur te registreren
* **Sitestructure items update** : geeft het recht sitstructuur items te bewerken
* **Sitestructure items delete** : geeft het recht content items uit de sitestructuur te verwijderen




