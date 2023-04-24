# Site inrichten

> [!info|label:Definitie]
> In de Redactie spreken we over een [site](/common/content/concept-site). Hieronder tonen we hoe je er één opzet en configureert. Met de term site hier bedoelen we niet een frontend website toepassing waar je via de browser naar surft. In deze context is een site, een container van content. Heel dikwijls gaat deze content wel gebruikt worden op een Website maar in essentie hoeft het niet. Het kan evengoed content zijn dat in een native app gebruikt gaat worden. 

Tenant beheerders maken [sites](/common/content/concept-site), die beheerd worden door [site beheerders](/redactie/content/toegang-site-beheerder). 

## Site aanmaken

* Open de [tenant](/common/content/concept-tenant) in kwestie
* Zorg ervoor dat de [talen](/redactie/content/inrichten-meertaligheid) op tenant niveau geconfigureerd zijn
* Open `Sites` vanuit het hoofdmenu
* Klik op `+ Nieuw maken`
* Geef een `Naam` op en de `Uurl` van de belangrijkste afnemer

> Even inzoomen op de `Url`: Doordat dit een headless systeem is, kunnen er meerdere afnemers zijn die dezelfde content willen gebruiken. Desondanks gaat er steeds één hoofd afnemer zijn waar de content effectief hoort. De Url hier zal als basis gebruikt worden voor heel wat [navigatie](/redactie/content/inrichten-navigatie) aspecten waaronder de url van content items.

* Selecteer minstens één taal uit de lijst. Staat er een taal niet bij, ga je dit eerst nog moeten [aangeven](/redactie/content/inrichten-meertaligheid)
* Klik op `Bewaar en ga verder` voor het volgende deel. 

Merk op dat nu de site **aangemaakt wordt**. Van zodra de klaar is, verschijnen er extra opties (tabs).

## Site id

Vanop de instellingen van de site kan je de Site Id kopiëren. Deze ga je op verschillend plekken kunnen gebruiken, vooral als je via de [WCM API](/wcmv4/README) content wil opvragen.

![Site id](../assets/site-id.jpg 'Site id kopieren')