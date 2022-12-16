# Core principes
De core principes van de WCM v4 / Redactie bepalen de werking van de modules en de interactie onderling.\
Het volgen van deze principes is noodzakelijk om een goed, stabiel en veilig werkend systeem te behouden.\
Er mag bij het ontwikkelen van (herbruikbare) contributies hier niet van afgeweken worden.

De Technical maintainer (Studio Hyperdrive) ondersteunt elke contributor d.m.v. een code review.\
Code die niet voldoet aan onderstaande principes zullen dan ook weerhouden worden voor een MTA of MTP (afhankelijk van de situatie).

## 1 Algemeen
Onderstaande core principes worden toegepast op alle componenten van de WCM v4 / Redactie.

### 1.1 Modules
De WCM v4 en Redactie zijn beide modulair opgezet.\
De core bevat bewust enkel de logica dat strikt noodzakelijk is om de modules in te laden en te ondersteunen in hun functionele noden.\
Dit betekent dat alle functionaliteit (backend en frontend) voorzien moet worden binnen zo'n modules.

### 1.2 Separation of concerns
#### Architecturaal
De WCM v4 en Redactie architectuur is opgedeeld in 3 lagen.\
Elke laag heeft een specifiek doel waarbij de componenten binnen deze laag niet buiten deze doeleinden mag vallen.\
Alle info over de lagen en hun doeleinden vind je hier: [Architectuur](/modules/content/architecture/index.md)

#### Inhoudelijk
Elke module beheert steeds 1 entiteit en zijn sub-entiteiten.\
Om te bepalen of iets in 1 module kan of best in een aparte module gebracht wordt kan je jezelf de volgende vragen stellen

1. Hebben de entiteiten iets met elkaar te maken?
2. Kan de ene entiteit werken zonder de ander mits hierop wordt voorzien?
3. Is een entiteit vervangbaar?
4. Is het technisch mogelijk om via de API van modules alle nodige samenwerking te doen indien deze modules opgesplits zijn

Op de laatste vraag is het antwoord technisch gezien meestal "ja" maar er moet natuurlijk wel rekening gehouden worden met de extra effort die nodig is om dat gedaan te krijgen.
We raden echter aan om die extra effort steeds te overwegen omdat het modulariseren van entiteiten (wanneer nuttig) een grote meerwaarde kan betekenen voor eindgebruikers, beheerders en de infrastructuur.

> [!info]
> Het opdelen van entiteiten in modules heeft een aantal belangrijke voordelen waardoor het opsplitsen van hoofdentiteiten zeker steeds overwogen moet worden:
> - De logica die binnen een tenant gebeurd kan gereduceerd worden tot wat echt nodig is voor die tenant
> - Gebruikers (redacteurs, content beheerders, ...) worden dan ook niet geconfronteerd met functionaliteit dat ze niet nodig hebben
> - Indien problemen ontstaan met een module kan de impact op gebruikers (redactie interface) en afnemers (websites, apps) enorm verkleind worden omdat zo niet alles breekt 
> - Resource wise kan er per module opgeschaald worden in de Kubernetes cluster. Hierdoor kan er heel fijnmazig gespeeld worden met resource mangagement overheen het platform.
> - Modules kunnen interne zaken beschermen t.o.v. andere modules en enkel acties toelaten die het wil. Dit heeft op zich een aantal eigen voordelen:
>   - De ontwikkelaars hebben steeds een duidelijk zicht op welke functionaliteit waar gebruikt kan worden. Er kan dus specifieke flows gevolgd worden bij debugging
>   - Modules kunnen geswapped met een andere module zolang ze dezelfde API voorzien. Dit zorgt ervoor dat een refactor heel beperkt blijft tot een module als een engine verandert.
>   - Ontwikkelaars gaan beter nadenken over de API die ze gaan exposen en bijgevolg meer nadenken in hergebruik om overweg te kunnen met bovenstaande zaken.

**Een voorbeeld: Content module**
- entiteit: content
- sub-entiteiten: veld-types, data-types, content-types, presets
- entiteiten die geen deel van de module mogen zijn: assets, sites, taxonomy, navigation

De redenering hier is dat content nooit kan leven zonder content-types, data-types, veld-types en presets maar wel kan bestaan zonder sites, assets, taxonomy en navigation.
#### Technisch
Ook binnen de modules raden we aan de deze principes door te trekken.\
De boilerplates kunnen hierin een handige leidraad in zijn.

### 1.3 Testing
In conformiteit met de Digipolis guidelines wordt er van alle backend modules verwacht om 80% test coverage te voorzien.\
Voor frontend integration testing zijn er om praktische redenen (modulaire setup) geen minimum coverage vereisten.\
Unit testing wordt wel verwacht op herbruikbare componenten.

> [!info]
> Om volledige integratie testen op de frontend mogelijk te maken, moet er complexe tooling voorzien worden die het mogelijk maakt om andere modules en het core systeem te mocken.
> Deze tools zijn er momenteel nog niet waardoor testing op de frontend zich enkel kan beperken tot unit testing.
> Naast het voorzien van deze tools wordt ook nog bekeken om te gaan werken met Cypress voor end to end testing in de toekomst.

### 1.4 Rollen & rechten
Er wordt verwacht dat **alle** mutatie acties beschermd worden achter een recht.\
Als een actie door iedereen mag gebeuren moet dat recht aan alle rollen gekoppeld worden i.p.v. geen rechten te checken.\
Dit maakt het mogelijk om acties later alsnog te gaan afschermen voor eventuele nieuwe rollen met minimaal of geen dev werk.

Er zijn hierop 2 uitzonderingen waarbij er alsnog geen rechten mogen nagegaan worden:
1. De mutatie moet gedaan kunnen worden via de wcm-proxy API
2. De actie mag gebeuren door gebruikers die geen tenant rol hebben

De rechten moeten nagegaan worden op zowel de frontend als de backend.\
Waarbij de backend ervoor zorgt dat actie niet gedaan kan worden en de frontend de gebruiker begeleidt in wat hij wel of niet kan doen.\
Dit kan door bijvoorbeeld acties te disablen of te verbergen op basis van deze rechten.

## 2 Redactie
Onderstaande core principes worden gehanteerd binnen de Redactie (frontend).

### 2.1 Vertalingen
Er wordt verwacht dat alle copy in de code gebruik maakt van translations via de translations module.\
Het gebruik hiervan zal het in de toekomst mogelijk maken om de Redactie interface in meerdere talen aan te bieden.\
Daarnaast zorgt dit er ook voor dat alle copy centraal beheerd wordt. Dit maakt het gemakkelijker voor minder technische mensen om hier de nodige aanpassingen aan te doen.

Dit is een relatief nieuw gegeven en werd ook in de core nog niet overal retroactief voorzien.\
Het is echter wel de bedoeling dat alle nieuwe integraties hier gebruik van maken (core en contributies).

Voor meer informatie over het gebruik hiervan, kan je terecht bij de geüpdatete boilerplate module en bijbehorende [documentatie](/modules/content/developer-guides/greetings/step-2-greetings-page?id=vertalingen).

### 2.2 APIs & connectors

Modules worden in een afgeschermde scope opgestart (via webpack bundles).\
Dit heeft als voordeel dat interne logica van een module niet beschikbaar is voor andere modules en dus niet verkeerd gebruikt kan worden.

## 3 WCM
De volgende principes worden gehanteerd binnen de WCM microservice architectuur (backend).

### 3.1 Multi-tenancy
De WCM Core is Multi-tenant. Deze multitenancy is volledig software matig. Dit betekent dat alle tenants op dezelfde fysieke (micro)services terecht komen.\
De module moeten dus overweg kunnen met de volgende gevolgen hiervaan:
- Een module instantie kan een request krijgen voor elke tenant (waarvoor de module is ingesteld).
- Een module moet altijd verwachten dat een actie in functie van een tenant gebeurd (uitzonderingen hierop moeten goed doordacht zijn)
- De Gateway doet reeds bepaalde validaties maar een module staat ook zelf in voor het nagaan of de request geldig is in context van de tenant. Hiervoor zijn de nodige tools voorzien. (zie [Greetings module gids](/modules/content/developer-guides/greetings/index.md))

### 3.2 Request validatie
Een BSL of Engine is in zijn basis niet meer of minder dan een losse service gehost binnen de VPN van Digipolis.\
Elke module moet dus zelf bepaalde validaties voorzien om te verzekeren dat ongewenste requests niet worden verwerkt.

Er zijn 2 manieren om dit te valideren:

#### JWT verificatie
De WCM gateway gaat bij elk request die het doorstuurt naar een module een Authorization header meesturen in een JWT formaat.\
Deze JWT tokens zijn gesigneerd met een private token van de WCM Gateway en kunnen gevalideerd worden via de publieke token van deze gateway om te verzekeren dat de requests de WCM gateway gepasseerd zijn.

De JWT token bevat inhoudelijk o.a.:
- De tenant key (zie hieronder)
- De User token (indien aanwezig)
- De client die de request uitvoert
- Het contract die gebruikt is geweest voor de request (proxy of admin)

Indien je met NodeJS werkt heeft het Technical maintainer team al de nodige tools voorzien om deze validatie uit te voeren.\
Meer uitleg hierover vind je [hier](/modules/content/developer-guides/greetings/step-4-greetings-endpoint?id=stap-2-module-beveiligen).

#### Tenant key verificatie
De JWT verificate verifiëert enkel of de request de WCM Gateway gepasseerd is maar deze verifiëerd niet of de module toegang heeft tot de tenant waarvoor deze request is uitgevoerd.

Hiervoor is een tenant key in het leven geroepen. Elke tenant krijgt zijn eigen tenant key toegewezen.\
Deze tenant key wordt gebruikt voor de interne communicatie binnen het WCM in functie van de tenant.\
De WCM gateway stuurt in de inhoud van zijn JWT token steeds tenant key waarvoor de request is gedaan.

> [!Warning]
> Een tenant key mag nooit buiten de WCM context gecommuniceerd worden!\
> Dit betekent dat tenant keys enkel gebruikt mogen worden bij communicatie tussen BSL's, Core componenten, WCM Admin en WCM Gateway (lees: geen Engines).
>
> Indien er een vermoeden is dat deze key in gedrang is gekomen moet zo snel mogelijk een nieuwe key gegenereerd worden voor deze tenant.\
> Dit kan via de WCM Admin interface gedaan worden door een WCM Admin.

Indien je met NodeJS werkt heeft het Technical maintainer team al de nodige tools voorzien om deze validatie uit te voeren.\
Meer uitleg hierover vind je [hier](/modules/content/developer-guides/greetings/step-4-greetings-endpoint?id=stap-2-module-beveiligen).

### 3.3 Interne communicatie (BSL => BSL)
Communicatie tussen BSL's kan gebeuren op 3 manieren:
- Via de WCM Gateway => **afgeraden om de gateway te besparen**
- Rechtstreeks gebruik makende van de verkregen JWT token & tenant key => context over request moet doorgegeven worden (user gegevens)
- Rechtstreeks gebruik makende van de tenant key => context over request moet niet doorgegeven worden (geen user gegevens nodig voor de actie)

### 3.4 Kafka
Event based communicatie gebeurt binnen de WCM enkel tussen de BSL's, WCM Core en WCM Core componenten.\
Deze services zijn de enige services die toegang krijgen tot de WCM kafka topics.

Er wordt typisch een topic voorzien per hoofd entiteit. Indien ["separation of concerns"](/modules/content/core-principles?id=_12-separation-of-concerns) regel gerespecteerd is, betekent dit meestal dat er een topic wordt aangemaakt per module.

Modules kunnen lees rechten krijgen op topics van andere modules maar hebben doorgaans enkel schrijfrechten op hun eigen topic.\
Op deze manier kan er tussen modules event based gecommuniceerd worden.

Het formaat van een module ligt ook vast. Meer info daarover kan je hier vinden [Event Registry](TODO).
