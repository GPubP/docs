# Definition of Done

Studio Hyperdrive, die de rol opneemt van Technical maintainer binnen het GPubP Content beheer platform, heeft de opdracht gekregen van Digipolis om steeds een code review te voorzien voor elke contributies.

Op deze manier willen we contributors bijstaan bij hun ontwikkelingen en ervoor zorgen dat de algemene beveiliging, core principes en best practices gehanteerd worden.

Voor elke MTA en MTP moet er een nieuwe review aangevraagd worden via Erik Lenearts <erik.lenearts@digipolis.be>.

> [!warning] Een aanvraag voor een review dient tijdig te gebeuren.\
> Er wordt sterk aangeraden om bij aanvang van het traject Studio Hyperdrive (via Erik) op de hoogte te houden van de verwachte review momenten.
> Op deze manier kan Studio Hyperdrive hiermee rekening houden in hun planning en zijn er geen onverwachte vertragingen.

Een review gaat een set van vaste en variabele parameters nagaan. 
Verder vind je de huidige vaste checklist die momenteel overlopen wordt.
Elke opmerking krijgt een van de volgende prioriteiten toegewezen:
- **Blocker**: Dit is heel belangrijk en zou idealiter nog voor de MTA moeten opgelost worden
- **Critical**: Dit is heel belangrijk en zou idealiter nog voor de MTP moeten opgelost worden
- **Major**: Sterke aanbevelingen maar kunnen, indien nodig, na MTP voorzien worden
- **Minor**: Wijzigingen die we aanraden maar maar in principe op de lange termijn kunnen opgelost worden, indien nodig.
- **Trivial**: Kleine optimalisaties die eigenlijk strikt gezien niet noodzakelijk zijn maar er wel voor zorgen dat de module iets beter gealigneerd is met de principes en best practices van de WCM

## Review checklist

> [!warning] Onderstaande lijst wordt regelmatige aangepast / aangevuld.\
> We raden aan om deze pagina regelmatig te raadplegen.

### 1. Security

#### 1.1 JWT Gateway validatie
!> Gemiddelde prio: **Blocker**

De JWT Gateway verificatie is heel belangrijk voor de veiligheid van de module en het WCM in het algemeen.\
De middleware functies, aangeboden door de “@wcm/config-helper”, zorgen ervoor dat enkel calls aanvaardt worden die eerst langs de WCM Gateway gepasseerd zijn of de juiste tenant key bevatten. 

Dit is belangrijk omdat de WCM gateway een aantal cruciale checks uitvoert voor de request doorgestuurd wordt naar de BSL module (zie ook [JWT Verificatie](/modules/content/core-principles?id=jwt-verificatie)): 
- Gaat op basis van de route, contract, tenant en credentials na of deze route wel toegankelijk is
- Vervangt een apikey (of application identifier) door een tenant context in de vorm van een JWT token

#### 1.2 Gebruik van security-rights
!> Gemiddelde prio: **Critical**\
Referentie naar richtlijnen: [Security-rights](/modules/content/core-principles?id=_14-rollen-amp-rechten)

Het gebruik van rechten wordt sterk aangeraden voor de meeste scenario's.

Door rechten te registreren is het  mogelijk om paginas, menu-items en calls af te schermen voor bepaalde gebruikers binnen een tenant (en bijgevolg ook site).

Indien er geen rechten worden geregistreerd en nagegaan, kan elke gebruiker binnen de tenant (ook al heeft hij geen rechten tot de site) bepaalde entiteiten van de service manipuleren.

#### 1.3 Correct gebruik van tenant apikey & context
!> Gemiddelde prio: **Blocker**

Het is heel belangrijk om correct om te gaan met de tenant apikeys en tenant context.

De tenant apikey zorgt ervoor dat er, binnen de context van een tenant, veilig tussen BSL services en hun engines gecommuniceerd kan worden zonder steeds via de Digipolis gateway en WCM gateway te passeren. Een voorwaarde voor de veiligheid van deze methode is dat er in geen enkel geval de apikey gebruikt wordt voor communicatie met services buiten de WCM context en dat deze apikey nooit in url paden terecht komen bij request (zodat deze niet gelogd worden)

De tenant apikey is geen vaste key en kan op elk moment gereset worden door een admin als blijkt dat de tenant key niet meer veilig is (bv. als er ontdekt wordt dat de apikey foutief gebruikt werd door een BSL module). Dit betekent dat je deze key niet kan gebruiken als vaste identifier.


#### 1.4 Correct omgaan met multi-tenancy
!> Gemiddelde prio: **Blocker**\
Referentie naar richtlijnen: [Multi-tenancy](/modules/content/core-principles?id=_31-multi-tenancy)

#### 1.5 Correct gebruik van credentials
!>Gemiddelde prio: **Blocker**

Zorg ervoor dat de credentials van Kafka, MongoDB en dergelijke steeds correct worden gebruikt.
Neem niet zomaar credentials over van andere services en zorg steeds voor eigen credentials per service / module.

### 2. Core principles

#### 2.1 Voorzien van testen
!> Gemiddelde prio: **Critical**\
Referentie naar richtlijnen: [Testing](/modules/content/core-principles?id=_13-testing)

#### 2.2 Request validatie
!> Gemiddelde prio: **Minor**

We raden aan om in elke stap (BSL en Engine) request body validatie te voorzien.\
Indien er gegruik gemaakt wordt van de boilerplate kan er gebruik gemaakt worden van dto's om dit te faciliteren (zie [NestJS Validation](https://docs.nestjs.com/techniques/validation)).

#### 2.3 Gebruik van vertalingen API
!> Gemiddelde prio: **Major**
Referentie naar richtlijnen: [Vertalingen](/modules/content/core-principles?id=_21-vertalingen)

Er wordt verwacht dat alle translations vanuit de translations module gehaald worden zodat deze in de toekomst centraal beheerd kunnen worden (via bv. een interface of download/upload principe). De registratie die nu gebeurd zorgt dat de keys gekend zijn en geeft een default waarde mee. Het is de bedoeling dat die in de toekomst overschreven kunnen worden, indien nodig.

Voor meer informatie over het gebruik hiervan, kan je terecht bij de geüpdate boilerplate module en bijbehorende [documentatie](/modules/content/developer-guides/greetings/step-2-greetings-page?id=stap-3-vertalingen).


#### 2.3 Monitoring endpoint
!> Gemiddelde prio: **Blocker**

Het correct voorzien van een monitor endpoint is verplicht.\
Dit endpoint wordt gebruikt om een algemene status per tenant te kunnen aanbieden aan Digipolis.\
Indien deze niet voorzien wordt zal de status permanent op rood staan op https://status.antwerpen.be (VPN nodig), wat niet de bedoeling is.

Zie de boilerplate voor een voorbeeld implementatie

### 2.4 APM integratie
!> Gemiddelde prio: **Critical**

Het is verplicht om APM te activeren op alle BSL'S en Engines gebruikt door het WCM.
Integratie met APM is heel gemakkelijk en is standaard voorzien in de BSL boilerplate.

1. Installeer de apm module
```bash
npm i apm-elastic-node@latest
```
2. Voorzie de volgende environment variabelen
```env
ELASTIC_APM_SERVER_URL=https://apm-app2-a.antwerpen.be
ELASTIC_APM_ACTIVATE=true
ELASTIC_APM_SECRET_TOKEN=[key]
ELASTIC_APM_CLOUD_PROVIDER=none
```
3. Voeg de volgende lijn toe aan een startup file in je service (bv. app.js in de boilerplate).
```js
require("elastic-apm-node").start();
```

### 3. Best practices

#### 3.1 Verwijzingen naar boilerplate
!> Gemiddelde prio: **Minor**

Zorg ervoor dat alle referenties en voorbeeld code uit je service gehaald is, indien je gestart bent vanuit een boilerplate.

#### 3.2 Hergebruik van stores (FE)
!> Gemiddelde prio: **Minor**

Het is nuttig om bij hergebruik van resources te evalueren of hier een eigen store voor opgezet moet worden of een hergebruikt kan worden vanuit andere modules.\
Hoewel een eigen store om deze op te halen perfect mogelijk is, zijn er voordelen aan het hergebruiken van stores en integraties van andere modules:
- Geen duplicatie van code
- Optimalisatie van request management door caching
- Eventuele API aanpassingen zijn makkelijker te beheren

#### 3.3 Correct gebruik van environment variabelen
!> Gemiddelde prio: **Minor**

De boilerplate voorziet een config folder dat environment variabelen omzet naar een configuratie object dat volledig getyped is.
We raden aan om deze te gebruiken want dat heeft de volgende voordelen:

- Het aanpassen van een env variabele hoeft maar op 1 plaats te gebeuren
- Er kunnen geen typo’s gebeuren bij het aanspreken van de config aangezien deze getyped is

#### 3.4 Correct gebruik van typings
!> Gemiddelde prio: **Minor**

We plaatsen hierbij gewoonlijk de volgende opmerkingen (indien relevant):

##### 3.4.1 Typings in aparte files
We verkiezen ervoor om interfaces & types steeds in een aparte [file].types.ts file te verwerken.\
Dit heeft dezelfde voordelen zoals aangehaald in [Beheer van constanten](/modules/content/oplevering/dod?id=_36-beheer-van-constanten).

##### 3.4.2 Hergebruik van typings
Er wordt geen gebruik gemaakt van de typings van de content en content-type module. Dit zorgt ervoor dat bij het wijzigen van de types dit in meerdere modules moet gebeuren.

##### 3.4.3 No any
Er wordt nog af en toe aan any typing gedaan.. Doorgaans wordt er aangeraden om alles te typen en nooit any of unknown te gebruiken, tenzij het niet anders kan (bv. externe library, te complexe generic typing, enz)

#### 3.5 Conformiteit met de linters
!> Gemiddelde prio: **Minor**

We raden aan om een linter te gebruiken voor oplevering en alle opmerkingen die daaruit komen te fixen.
Indien gestart wordt vanuit een boilerplate, kan je het volgende commando gebruiken:
```bash
npm run lint
```

#### 3.6 Beheer van constanten
!> Gemiddelde prio: **Trivial**

We raden aan om constanten in aparte files te steken [component|entiteit].const.ts.\
Dit is zorgt ervoor dat deze waarden steeds op een vaste plaats te raadplegen zijn.\
Als deze waarden op een consistente plaats bewaard worden, zijn ze gemakkelijker terug te vinden achteraf.

#### 3.7 Gebruik van functional components (FE)
!> Gemiddelde prio: **Minor**

Er is binnen GPubP Content beheer gekozen om altijd met functional components te werken en niet met class based components. Hierdoor volgen we de voorkeur van de React community en heeft bijgevolg de volgende voordelen:
- Code snippets kunnen gemakkelijk overgedragen worden van de ene naar de andere component
- Documentatie van zowel GPubP Content beheer als externe libraries zijn gemakkelijker om van over te nemen
- Code is leesbaarder voor iedereen vanwege consistentie
- Door steeds op dezelfde manier te werken, reduceren we de kans op bugs



