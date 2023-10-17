# API contract

In grote lijnen loopt het bekomen van een contract als volgt 

1. [Definieer je app in het open platform](/wcmv4/content/api-contract?id=app-definiëren-in-het-open-platform)
2. [zoek je API in de marketplace en vraag een contract aan](/wcmv4/content/api-contract?id=zoek-je-api-en-vraag-een-nieuw-contract-aan)
3. [Vraag aan een tenant beheerder om je toepassing aan een tenant te koppelen.](/wcmv4/content/api-contract?id=toegang-tot-tenant-aanvragen)
4. (optioneel) App Config instellen


## App definiëren in het open platform
Ga naar http://publisher.digipolis.be en registreer je afnemer die de API gaat afnemen. Dit levert je een `moniker` op zoals **classical-sin**.

* Zorg dat je een **Team** hebt waaronder deze registratie gaat maken
* Kies je type zoals **Web Frontend**

![Publisher](../assets/publisher-registratie.jpg 'Registreer een afnemer in de publisher.')

## Zoek je API en vraag een nieuw contract aan

Ga naar https://marketplace.digipolis.be en zoek je API (check de [beschikbare endpoints hier](/wcmv4/content/endpoints)). Vraag een contract aan voor de App die je net hebt aangemaakt en wacht totdat deze is goedgekeurd. 

![Marketplace](../assets/marketplace-contract-request.jpg 'Vraag een nieuw contract aan')

## Toegang tot tenant aanvragen

De WCM heeft een eigen Gateway, bovenop de API gateway. Hiermee regelen we welke afnemer mag werken met welke tenant. 

Vraag aan de [tenant beheerder](/redactie/content/toegang-tenant-beheerder) om je [toepassing rechten te geven](/redactie/content/inrichten-tenants?id=toegang-geven-voor-afnemers). Geef hierbij:
- Van welke tenant wil je data opvragen
- Wat is de naam van de toepassing die data gaat opvragen 
- de `moniker` van het open platform, deze kan je makkelijk kopiëren vanop de publisher toepassing.

![Publisher](../assets/publisher-copy-moniker.jpg 'Kopieer de moniker van de publisher')

## App config opzetten (optioneel)

!> Deze stap is nodig als je [content wil bewerken](/wcmv4/content/content-write).

Zet je een app op in app config (op ACC en/of PROD). Stel onder de Advanced Settings de identifier in als volgt:

* **Organisation ID:** `openplatform` *letterlijk overnemen*
* **Application ID:** `<moniker>`
* **Version ID:** `v1` *letterlijk overnemen* 

![API config](../assets/api-config.jpg 'API config')