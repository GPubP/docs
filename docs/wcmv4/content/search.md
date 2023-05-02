# Search API

De Search API is geen onderdeel van de WCM API. Veel zaken zoals taxonomy en navigatie zijn achterliggend andere subsystemen en de WCM API ontsluit deze voor de afnemers. 

> [!warning] 
> We hebben beslist dat afnemers **rechtstreeks** de Search API van Elastic zelf aanspreken. Op deze manier kunnen afnemers maximale snelheid bekomen wat essentieel is in search scenario's zoals o.a. het produceren van suggestielijsten in een autocomplete veld. 

## Index keuze

Elke site kan één of meerdere search indexen bevatten. Dit wordt door de [Site beheerder hier ingericht](/redactie/content/inrichten-search). 

In veel gevallen zal de `index` die je zal gebruiken voor je zoekopdrachten uit de WCM komen. Hiervoor maken [content beheerders](/redactie/content/toegang-content-beheerder) vaak een specifiek [content type](/redactie/content/inrichten-content-types) dat ze **zoekpagina** of **lijstpagina** noemen. Hier voegen ze een [zoekindex referentie](/redactie/content/inrichten-cc-zoekindex-referentie) content component toe waarmee de keuze van de index vastgelegd kan worden.

> Als we hier spreken over een `index` hebben we het wel degelijk over het index object dat [ingericht wordt](/redactie/content/inrichten-search) door de site beheerder. Deze features komen uit de [Search module](/modules/content/modules/module-search). Achterliggend is er voor elke index één op één een **Elastic App Search engine**.

Stel dat er een content item is **lijstpagina kantoren** waarbij de index **e-loket** is. Als je het [content item opvraagt](/wcmv4/content/content-item-read) krijg je de achterliggende Elastic App Search engine key.

```json
{
  "_id": "60b9ec5811264300093a98e2", 
  "uuid": "0d37b868-5e76-405f-9f2c-faf3f2e4de13",
  "fields": {
    ...
    "index-referentie": "wcm-e-loket-mijnsite-be-pza-production" 
    ...
  },
  "meta": {
    ... 
  },
}
```

> De naam van deze zoekindex referentie is de naam van de engine, deze wordt door de Elastic module bepaald, [lees er hier meer over](/redactie/content/inrichten-search). 

## Zoeken via de Search API

In de meest essentiële vorm zal je zoekopdracht er ongeveer als volgt uitzien:

```shell
POST 'https://appsearch-ent1.antwerpen.be/api/as/v1/engines/{engine}/search' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer {bearertoken}' \
--data '{
    "query": "something"
}'
```

De `bearertoken` kan je vragen aan een owner of admin van Elastic App Search die voor jou een `Public Search key` kan opzetten. Hij/zij zal je vragen voor welke engine je toegang nodig hebt. 

?> Meer info over de Search API van Elastic App Search kan je hier terugvinden: https://www.elastic.co/guide/en/app-search/current/search.html

