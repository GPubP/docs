# Frontend beheer

## Intro

Een `frontend` is de applicatie die de content rendert en presenteerd aan de eindgebruiker zoals de antwerpen.be portaal app of de visit app.

Frontends worden telkens op maat gemaakt door ontwikkelaars. Die kunnen gebruik maken van het GPubP Layout Rendering Framework.

## Layout Rendering Framework

Dit bestaat uit:

* Layouts
* Widgets
* Layout Renderer

### Layouts

Layouts worden door ontwikkelaars gemaakt en bevatten:

* bepalen de opmaak van een pagina
* geven aan waar welke widget komt te staan op die pagina
* zijn geschreven in json
* volgen deze [notatie specificatie](https://layout-renderer-a.antwerpen.be/docs/%5B%22core%22%2C%5B%22layout-spec%22%2C%22md%22%5D%5D).

!> todo: voeg een voorbeeld toe van een layout

### Layout Library

?> We voorzien in de toekomst een bibliotheek van layouts die telkens terugkomen in de verschillende frontends.

### Widgets

Het effectief renderen van content gebeurt door de widgets. Deze worden gemaakt door ontwikkelaars en:

* zijn core branding compliant
* WCAG compliant
* zijn generiek inzetbaar en dus herbruikbaar
* kunnen specifiek gemaakt zijn voor één frontend
* bevatten dikwijls verschillende weergave opties

!> todo: voeg een voorbeeld toe van een widget

### Widgets library

Alle generieke widgets kan je terugvinden in de Widgets Library

!> Todo: zet hier de link naar de widgets library

### Layout Renderer

Dit is de motor die de rendering voor zich neemt. De layout renderer is een package dat als onderdeel mee draait in de frontend applicatie.

Het rendereren gebeurt typisch als volgt:

* er is een layout waar de structuur en de widgets op gespecifieerd zijn
* content wordt opgehaald
* de combinatie van layout, widgets en content wordt gerenderd

De layout Renderer:

* kan gebruikt worden in een React toepassing
* kent een principe van datastores die achterliggende bronnen kunnen bevragen (zoals de WCM)

![GPubP frontend ](../assets/gpubp-frontend.jpg 'High level overzicht van frontend beheer in GPubP')
