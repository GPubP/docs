# Tenant inrichten

> [!info|label:Definitie]
> Een **tenant** is de een afgebakende omgeving dat uit één of meerdere sites bestaat. [Meer info](/common/content/concept-tenant).


Het eerste wat je moet doen om een [tenant](/common/content/concept-tenant) te kunnen inrichten is toegang krijgen tot de tenant als [tenant beheerder](/redactie/content/toegang-tenant-beheerder). Volg hiervoor [deze procedure](/redactie/content/toegang-aanvragen)


## Nieuwe tenant aanvragen

Je kan ook een nieuwe tenant aanvragen via [dit formulier](https://formulieren.antwerpen.be/v1/generiek-eloket/aanvraag-nieuwe-tenant-gpubp). Merk op dat je niet zomaar een nieuwe tenant zal krijgen vermits dat het toch behoorlijk wat resources verbruikt. Bovendien zal je eerst een intake gesprek moeten houden om na te gaan of je recht hebt op een nieuwe tenant. Tijdens een intake gesprek kan je toelichten wat je plannen zijn en kunnen we nagaan of het systeem voor jou toereikend is, [wat er zit aan te komen](/RELEASE) en wat de timing van je project is.

> Contacteer de [product owner](/CONTRIBUTING?id=maintainers) voor intake gesprek.

## Modules activeren

Bij de aanvraag van een tenant kan je aangeven welke [modules](/modules/README) je wenst te gebruiken. Bestaat je tenant reeds, dan kan je alsnog bijkomende modules laten activeren voor je tenant.

Bekijk hier de volledige lijst van [bestaande modules](/modules/content/wcm-modules).

## Toegang geven voor afnemers

Via de [WCM admin](https://wcm-admin.antwerpen.be) toepassing kan je een `Server credential` toevoegen. 

Je kan op 2 manieren de afnemer identificeren:

1. via de afnemer z'n `Application Identifier` (voorkeur)
2. via de afnemer z'n `API key`

Bij elke API call zal de afnemer de `API key` mee geven. De API gateway zal deze call verrijken met de `moniker` (= application identifier) op basis van een [goedgekeurd contract](/wcmv4/content/api-contract). Beide identifiers zijn bruikbaar. Wij geven de voorkeur aan opzetten van toegang op basis van de `Application identifier`. Een `API key` kan makkelijker wijzigen (b.v. door een reset van deze key na compromitatie), de `moniker` blijft stabiel. 

> Merk op dat afnemers nooit zelf deze `moniker` kunnen meegeven, dat kan alleen de API gateway.

Vergeet zeker niet de nieuw aangemaakte credential te `enablen` via het vinkje bovenaan.

![WCM Admin](../assets/wcm-admin-server-credential.jpg 'Server credential via WCM Admin')

## Tenant specifieke instellingen 

Eenmaal de tenant up & running is en je bent aangemeld als tenant beheerder kan je enkele tenant specifieke instellingen opzetten zoals: 

* [Talen](/redactie/content/inrichten-meertaligheid)
* [Sites](/redactie/content/inrichten-sites)
* [Workflows](/redactie/content/inrichten-workflows)
* Structuur elementen zoals [content types](/redactie/content/inrichten-content-types), [blokken](/redactie/content/inrichten-content-types), [compnenten](/redactie/content/inrichten-cc) & [Taxonomie](/redactie/content/inrichten-taxonomie)
* Gebruikers
* Events