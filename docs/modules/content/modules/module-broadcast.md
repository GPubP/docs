# Broadcast module

> [!info|label:Definitie]
> Met deze module kan je content **broadcasten** naar een specifieke afnemer. Het is origineel ontworpen voor het verzenden van gepubliceerde naar een e-mail campagne systeem voor het automatisch versturen van e-mail nieuwsbrieven voor het burgerportaal van Politiezone Antwerpen.

## Verzendkanalen
De essentie van deze module is om gepubliceerde content te verzenden. Als [Content beheerder](/redactie/content/toegang-content-beheerder) kan je een verzendkanaal opzetten. Hiermee kan je instellen 
- wat willen we verzenden, i.e. welke content
- wanneer willen we dit verzenden
- naar waar willen we dit verzenden
- op welke wijze willen we dit verzenden.

### Nieuw verzendkanaal maken 

Om een verzendkanaal te maken ga je hiervoor naar je site en selecteer `Content > Content verzenden`. 

![Content verzenden menu](.//modules/assets/broadcast-module-1.jpg 'Menu van de broadcast module.')

Hier kom je terecht op het overzicht van de verzendkanalen. 

![Overzicht verzendkanalen](.//modules/assets/broadcast-module-2.jpg 'Verzendkanalen overzicht.')

### Bestemming inrichten
Momenteel is er één bestemming die gebruikt kan worden om content naar te versturen, nl. het e-mail marketing product `Sendgrid`. 

> [!note] 
> De broadcast module is wel uitbreidbaar gemaakt zodat nieuwe bestemming ingeplugd kunnen worden. 

#### Sendgrid bestemming
Als de broadcast module content verzend naar Sendgrid zal deze laatste die inhoud samenvoegen met een gekozen e-mail template en de e-mails versturen naar de gekozen verzendlijst(en). Op deze manier kunnen we vanuit één bron (WCM) zowel content voor een website als voor nieuwsbrieven voorzien.

Vraag een nieuwe `API key` aan in Sendgrid en vul deze als eerste in. Als deze key geldig is en voldoende rechten heeft kan je verder. 

* Het systeem zal dan alle **verzendlijsten** ophalen uit Sendgrid waaruit je kan kiezen. Deze verzendlijsten vind je in Sendgrid onder `Marketing > Contacts`. 
* Vervolgens kies je een **e-mail template**. Deze vind je in Sendgrid onder `E-mail API > Dynamic templates`. 
* De **afzender** kan je kiezen uit een lijst, deze vind je in Sendgrid onder `Settings > Sender authentication`. 
* Het **onderwerp** kan je vrij invullen, dit wordt het onderwerp van de e-mails die verstuurd worden door Sendgrid. 

![Sendgrid bestemming](.//modules/assets/broadcast-module-3.png 'Sendgrid bestemming.')

> [!warning] 
> Vergeet je instellingen niet te **bewaren** en je kanaal te **activeren** (zie `Instellingen > algemeen` ).

### Content kiezen

Maak je keuze in de lijst van **[content types](/common/content/concept-ct) en [blokken](/common/content/concept-cb)**. Dit betekent dat enkel die content zal behandeld worden in dit verzendkanaal.

![Kies je content](.//modules/assets/broadcast-module-4.jpg 'Content keuze van het verzendkanaal')

Onderaan kan je aangeven hoe **content klaargezet wordt** om te verzenden:
* **Automatisch**: Telkens wanneer een redacteur een [content item](/common/content/concept-ci) publiceert zal deze automatisch klaar gezet worden in dit kanaal.
* **Manueel**: Content beheerders kiezen zelf welke content ze willen klaarzetten.

### Verzendwijze

Als laatste stap stel je **de wijze van verzending in**. Hier heb je keuze tussen: 

* **Apart**: Elk content item dat klaargezet wordt, zal apart verzonden worden
* **Samen**: Meerdere Content items worden klaargezet en worden samen aan de bestemming overhandigd. Dit is o.a. handig om meerdere content items tesamen in één nieuwsbrief te plaatsen dat via Sendgrid verstuurd wordt.

![Verzendwijze](.//modules/assets/broadcast-module-5.jpg 'Verzendwijze instellen van het verzendkanaal')

> [!info|label:Tip]
> Bij de verschillende verzendwijzen heb je nog verdere keuze om onmiddelijk of uitgesteld te verzenden alsook te verzenden op een gegeven tijdstip of vanaf een gegeven aantal.

## Verzendkanaal inhoud beheren
Eenmaal de instellingen van je verzendkanaal ingericht zijn kan je ermee aan de slag. 

Bovenaan de inhoud tab zie je een samenvatting van de instelling, ook handig ingeval je zelf geen rechten hebt om de instellingen te bekijken/bewerken. 

![Inhoud van het verzendkanaal](.//modules/assets/broadcast-module-6.jpg 'Inhoud van het verzendkanaal')

Onderaan kan je zelf manueel naar content items zoeken en deze **toevoegen aan de inhoudslijst**. Of ze nu automatisch of manueel zijn toegevoegd, het is van hieruit dat je deze lijst kan beheren. Zo kan je er content items uithalen (individueel of in bulk) alsook herplannen (individueel of in bulk).

![Inhoud van het verzendkanaal](.//modules/assets/broadcast-module-7.jpg 'Inhoud van het verzendkanaal')

## Verzendkanaal testen
Om te zien welke inhoud er nu effectief naar de bestemming verstuurd wordt, kan je gebruik maken van de test functie. Onderaan kan je zelf kiezen welke content je wil opnemen in de test. Als je op `Versturen` klikt zal deze inhoud effectief worden overhandigd aan de ingesteld bestemming van dit verzendkanaal. 

![Testen van het verzendkanaal](.//modules/assets/broadcast-module-8.jpg 'Testen van het verzendkanaal')


?> Ga terug naar het [overzicht van alle modules](/modules/content/wcm-modules)