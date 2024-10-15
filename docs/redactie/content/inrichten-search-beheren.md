# Indexen beheren

> Kijk hier om de [Search voor te bereiden](/redactie/content/inrichten-search-voorbereiding) en hier voor [enkele basis concepten](/redactie/content/inrichten-search-indexvsengine).

## Index aanmaken in de Redactie

1. Ga naar de Redactie
2. Ga naar een tenant
3. Open de inhoud van een site
4. in het hoofdmenu vind je onder `Instellingen > Elastic App Search`
5. Click op `+ Index aanmaken`
6. Geef de index een naam en een omschrijving.
7. Klik op `Bewaar en ga verder`

Je krijgt een boodschap dat de index is aangemaakt zoals in onderstaande screenshot:

![Nieuwe index](../assets/search-index-create.jpg 'Index succesvol aangemaakt')

In essentie kan je hier al ophouden met configureren. Er wordt standaard al heel wat achter de schermen voor je gedaan waaronder:

* Alle [content types](/common/content/concept-ct) worden automatisch mee opgenomen in de index (geen [content blokken](/common/content/concept-cb)).
* Voor elk content type dat opgenomen is in de index wordt de titel en teaser reeds standaard mee opgenomen.

### Wat wordt er geïndexeerd?

**Per index** kan je bepalen wat er geïndexeerd wordt. Je kiest zelf de content types die je wil opnemen in de Elastic App Search engines.

1. Open de details van een index in de Redactie
2. Klik op de `content` tab

Hier zie je 2 lijsten `Indexeren` en `Niet indexeren`. Wat in de bovenste lijst staat wordt mee opgenomen, wat in de onderste lijst staat niet.
Je kan via het `vuilbak` en `+` icoon kiezen of je content mee wil opnemen of niet. 

![Index content](../assets/search-index-content-overview.jpg 'Content overzicht van een index')

Je kan nog verder gaan en bepalen wat je precies van een content type wil opnemen in de Elastic App Search enige.

1. Open de details van een index in de Redactie
2. Klik op de `content` tab
3. Kies een content type uit de lijst `indexeren` en klik op de naam

Hier kan je via een schakelaar bepalen of het mee opgenomen wordt in de index of niet. In essentie is het hetzelfde als in het vorige scherm dit content type in de bovenste of onderste lijst te plaatsen.

![Index content](../assets/search-index-contenttype-overview.jpg 'De content types die geïndexeerd gaan worden')

4. klik vervolgens op de `componenten` tab

Hier zie je het overzicht van alle componenten. Ook hier maken we gebruik van 2 lijsten. een bovenste lijst wat mee geïndexeerd gaat worden en de onderste lijst niet. Zelfste patroon via het `vuilbak` en `+` icoon om de indexering aan te passen.

![Index componenten](../assets/search-index-contenttype-details.jpg 'De componenten van een content type die geïndexeerd gaan worden')

5. Kies uit de lijst onderaan een component uit en druk op de `+` knop.

Het component zal zich ontvouwen en je kan hier kiezen **hoe** je de inhoud wil opnemen in Elastic App Search.

![Index content](../assets/search-index-contenttype-component.jpg 'Component mee opnemen in de index')

Eerst kies je de `indexering methode` en vervolgens het `veld in Elastic` waar de inhoud wordt geplaatst.
Soms kan je niets kiezen zoals in de afbeelding hierboven waar je een taxonomie wil opnemen in de index.
Hier heb je geen keuze; er is maar één manier hoe het systeem weet om taxonomie info op te nemen.

#### Search Mappers

Soms kan je kiezen uit meerdere methodes. Achterliggend spreken we over `Search Mappers`. Deze zijn gelinked aan een content component. Dus voor Taxonomie is er maar één Search mapper 'Taxonomy mapper'.
Voor een tekstveld zijn er bv 2 methodes i.e. een 'value mapper' of 'tekst mapper'.

* **Value Mappers**: Alle content componenten hebben een value mapper. Deze gaat de (json) data as-is overzetten naar Elastic.
* **Specifieke mappers**: Dit zijn de mappers die het systeem reeds kent:

| Mapper | Content componenten | Veld in EAS | Wat wordt overgezet? |
|---|---|---|---|
| Afbeelding mapper | [Afbeelding](/redactie/content/inrichten-cc-afbeelding) | te kiezen | Een JSON met url's van de originele afbeelding en crop varianten. |
| Hoofdafbeelding mapper | [Afbeelding](/redactie/content/inrichten-cc-afbeelding) | `image` | Een JSON met url's van de originele afbeelding en crop varianten.  |
| Taxonomie mapper | [Taxonomie](/redactie/content/inrichten-cc-taxonomie) | `tax_<naam>`, `tax_labels` | Taxonomie data wordt in 2 velden gesplitst.In de eerste komen de taxonomie term id's, in de 2e de verzameling van labels |
| Titel mapper | Standaard titel | `title` | Zet de titel (enkel tekst) van een content item naar dit veld. |
| Teaser mapper | Standaard tekstvak met opmaak, [Open Graph Protocol](/redactie/content/inrichten-cc-opengraph) | `teaser` | Zet de teaser (enkel tekst) van een content item naar dit veld. |
| Text mapper | [Tekstlijn](/redactie/content/inrichten-cc-tekstlijn), [Tekstvak](/redactie/content/inrichten-cc-tekstvak), [Tekstvak met opmaak](/redactie/content/inrichten-cc-tekstvak-met-opmaak), [Keuzerondje](/redactie/content/inrichten-cc-keuzerondje), [Nummer](/redactie/content/inrichten-cc-nummer), [Keuzelijst](/redactie/content/inrichten-cc-keuzelijst), [Keuzevakje](/redactie/content/inrichten-cc-keuzevakje), [Telefoonnummer](/redactie/content/inrichten-cc-telefoonnummer), [e-mail](/redactie/content/inrichten-cc-email), [Adres](/redactie/content/inrichten-cc-adres) | te kiezen | Extract de tekst van het content component en zet deze over. |
| Value mapper | Alle componenten | te kiezen | Gaat de JSON as-is overnemen. |

#### Meta data

Naast de content componenten die je kiest om mee op te nemen in de index, zal het systeem zelf volgende data altijd mee opnemen in de engine(s) van Elastic App Search: 

| meta data 	| Omschrijving 	| Voorbeeld 	|
|---	|---	|---	|
| id 	| uniek id van het content item 	| fff93724-ca03-4b34-98d4-3f83fe0bdc81 	|
| site 	| naam van de site in de Redactie 	| politieantwerpen.be 	|
| app 	| Geeft aan dat deze data van de WCM komt van de gegeven tenant en site 	| WCM_pza_politieantwerpen.be 	|
| group_field 	| Geeft het soort content aan, voor de WCM is dit het content type 	| briefing_bericht 	|
| content_type_id 	| Geeft de id van het content type in de WCM 	| 76ec13db-d6b4-43f8-a9e3-b18f6b45166e 	|
| user_roles 	| Voor backwards compatibiliteit 	| ["anonymous"] 	|
| lang 	| De taal van deze content 	| nl 	|
| last_indexed 	| Wanneer is dit content item voor het laatst geïndexeerd? 	| 2023-02-27T14:01:41.382Z 	|
| created 	| Wanneer is dit content item gemaakt in de Redactie 	| 2022-11-08T08:35:06.918Z 	|
| last_modified 	| Wanneer is dit content item laatst aangepast in de Redactie 	| 2022-11-08T08:36:18.304Z 	|
| issued_on 	| Wat is het uitgifte tijdstip van dit content item 	| 2022-11-08T08:36:18.304Z 	|
| first_published 	| Wanneer is dit content item eerst gepubliceerd? 	| 2022-11-08T08:36:18.304Z 	|
| url 	| De volwaardige, absolute url naar het content item in de frontend 	| https://www.politieantwerpen.be/nieuws/man-die-kattenbakvulling-op-straat-gooit-is-gevat 	|
| raw 	| De volledige JSON data zoals ze uit de WCM API komt. 	| { ... } 	|
| body 	| De verzameling van alle tekstuele informatie aan elkaar geplakt zonder enige vorm van opmaak. Ideaal om een full text search op te baseren. 	| lorum ipsum 	|

## Index activeren

Wanneer een index gemaakt wordt zal deze by default **niet geactiveerd** zijn. Dit hebben we gedaan zodat je zelf eerst de configuratie kan bekijken en aanpassen daar waar nodig.

> [!warning|label:Activeer je index]
> Vergeet niet je index te activeren wat erop neerkomt dat vanaf dan alle content dat gepubliceerd wordt mee zal opgenomen worden in je index.

## Herindexeren

Soms is er al content dat bestaat vooraleer je een index maakt. Soms heb je een index tijdelijk gedactiveerd. In deze gevallen kan je via herindexeren alle content van de Redactie opnieuw overlopen en overzetten naar Elastic App Search. 

Hiervoor zie je in het overzicht het verschil tussen hoeveel online content items er in de Redactie zitten en hoeveel in Elastic App Search.

![Index content](../assets/search-index-content-overview.jpg 'Content overzicht van een index')

Je kan kiezen om **partieel te herindexeren** of de **volledige index**. In het eerste geval kan je bv één content type herindexeren van de index.

> [!info|label:Wat gebeurt er met herindexeren]
> Een herindexatie zal de engine behouden maar (partieel) leegmaken om daarna terug op te vullen. Alle settings zoals schema, tuning, synoniemen etc blijven met andere woorden behouden.

## Indexen aanpassen en verwijderen

Als je bovenstaande gelezen hebt zal je nagenoeg elk scherm al gezien hebben om de info van een index op te vragen en aan te passen.

!> Wil je een index **verwijderen**, dat kan. Let er wel op dat alle respectievelijke Elastic App Search engines mee verwijderd zullen worden. Alle configuratie dat je in Elastic App Search gedaan hebt zal bijgevolg verdwenen zijn.

> [!info|label:Hoeveel indexen maak je best]
> Je kan kiezen om één index te maken waar alle content samen zit of meerdere indexen met elks een deel van de content. Wat is het beste? Wel, dit hangt af van:
> 
> * **Search relevantie tuning:** je wil gewichten en boosts anders inrichten 
> * **Synoniemen:** de situatie vereist andere synoniemen, zo is `bank` iets heel anders in een recreatieve context of een financiële context.
> * **Curations:** Je wil voor specifieke zoektermen, andere pagina's vastpinnen bovenaan de zoekresultaten
> 
> In essentie maak je een nieuwe index als je voor één van deze redenen wil afwijken van reeds bestaande indexen.

## Rechten

TODO

?> Zie ook de [Search API](/wcmv4/content/search).
