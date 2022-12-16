# Deploy
Een deploy van je contributie module kan aangevraagd worden en wordt praktisch uitgevoerd door de Technical Maintainer (SHD) op de acceptatie en productie omgeving.
Op de development omgeving wordt er verwacht dat de contributor dit zelf voorziet.

## Development
1. Vraag rechten aan voor de development omgeving van de WCM Admin interface (via Servicedesk \<servicedesk@digipolis.be\>)
2. Zet een module op binnen deze omgeving volgens de stappen beschreven in "[Modules opzetten](/modules/content/setup/wcm/modules)"

## Acceptatie

### Aanvragen
Een nieuwe aanvraag voor een MTA gebeurd steeds per mail via Erik Lenearts \<erik.lenearts@digipolis.be\>.

> [!warning]
> We raden aan deze vraag zo vroeg mogelijk in te plannen om niet voor verassingen te staan.

### Wat verwachten we van jou
1. Een reeds geconfigureerde opzet op development
2. Een geslaagde [review](/modules/content/oplevering/review) (geen blockers)
3. Een indicatie wanneer jullie of de business verwacht dat de module getest kan worden op acceptatie
4. En lijst van modules die moeten overgezet worden naar acceptatie\
    4.1 De modules (namen + versie in dev) die ingesteld moeten worden naar acceptatie\
    4.2 De url's waarop de BSL en engine services beschikbaar zijn\
    4.3 De apikey's die gebruikt worden om de WCM Modules Admin API aan te spreken\
5. De tenants waarop deze module geactiveerd moet worden
6. Beschikbaarheid van een dev om de services te deployen na de juiste instellingen zijn gedaan op acceptatie

### Wat mag je verwachten
Indien alle verwachtingen zijn ingelost, krijg je bij het resultaat van de review een datum (en tijd) waarop de module naar acceptatie gebracht kan worden.

## Productie

### Aanvragen
Een nieuwe aanvraag voor een MTP gebeurd steeds per mail via Erik Lenearts \<erik.lenearts@digipolis.be\>.

> [!warning]
> We raden aan deze vraag zo vroeg mogelijk in te plannen om niet voor verassingen te staan.

### Wat verwachten we van jou
1. Een reeds geconfigureerde opzet op acceptatie
2. Een geslaagde [review](/modules/content/oplevering/review) (geen blockers en criticals)
3. Een indicatie wanneer jullie of de business verwacht dat de module naar productie gebracht worden
4. En lijst van modules die moeten overgezet worden naar productie\
    4.1. De modules (namen + versie in dev) die ingesteld moeten worden naar productie\
    4.2. De url's waarop de BSL en engine services beschikbaar zijn\
    4.3. De apikey's die gebruikt worden om de WCM Modules Admin API aan te spreken
5. De tenants waarop deze module geactiveerd moet worden
6. Beschikbaarheid van een dev om de services te deployen na de juiste instellingen zijn gedaan op productie
7. Een replica van de repository van de frontend modules met API documentatie, gehost op de Digipolis GPubP Github organisatie.

### Wat mag je verwachten
Indien alle verwachtingen zijn ingelost, krijg je een geplande MTP datum (of streefdatum).\
Deze datum zal doorgaans plaats vinden op een reeds geplande MTP datum.\
In samenspraak kan (in unieke gevallen) beslist worden om een aparte MTP te voorzien voor de contributie module
