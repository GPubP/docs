# Authenticatie & authorisatie voor API calls 

1. [content lezen](/wcmv4/content/api-authenticatie?id=content-lezen)
2. [content bewerken](/wcmv4/content/api-authenticatie?id=content-bewerken)

## Content lezen

Zorg ervoor dat je een geldig [contract](/wcmv4/content/api-contract) hebt. Je krijgt hiervoor een `API key`, deze vind je: 

* in de Publisher van het open programma
* onder de instellingen van de app (registratie)
* bij `Client keys` 
* onder de kolom `Client key`

![Publisher](../assets/publisher-client-key.jpg 'Client keys in de publisher')

!> **Geef bij elke API call deze `apikey` mee**. Zonder deze sleutel weet de WCM Gateway niet wie afnemer is die de request uitvoert. 

?> Done, nu kan je aan de slag en [API calls](/wcmv4/content/content-read) uitvoeren om content te lezen.

## Content bewerken (extra stappen)

Wanneer je content gaat bewerken via het [WCM Content Manager endpoint](/wcmv4/content/endpoint-content-manager) zal je bijkomende stappen moeten ondernemen, namelijk: 

1. [BRaaS inrichten](/wcmv4/content/api-authenticatie?id=braas)
2. [Authorisatie in de redactie inrichten](/wcmv4/content/api-authenticatie?id=redactie-configureren) 


### BRaaS
In BRaaS zal je een `AcpaaSConsumerApplication` moeten aanvragen zodat hier de rechten aan gekoppeld kunnen worden.

Hiervoor stuur je best een e-mail naar **servicedesk@digipolis.be** met de volgende vraag. 

```
Beste,

Kan je in BRaaS een subject van het type ‘AcpaaSConsumerApplication’ toevoegen voor “openplatform.<moniker>.v1” door een bijhorende Application aan te maken vanuit appconfig-application <url-appconfig-application>
de application identifier voor dit subject aanpassen zodat enkel de moniker overblijft via deze API call: 
curl --location -g --request POST 'https://api-gw-<a|p>.antwerpen.be/acpaas/braas/v3/subjects' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Bearer token>' \
--header 'apikey: <apikey>' \
--data-raw '{"subject": {
        "address": null,
        "domain": null,
        "email": null,
        "externalMutableReference": "<moniker>",
        "firstname": null,
        "id": "app-b8b56ce3-53fd-...-8e0f-a584f6dfaf50",
        "lastname": "SPO",
        "nickname": null,
        "type": "ACPaaSConsumerApplication",
        "username": "<afnemer applicatienaam>"
    }
}'

Kan je dit nieuwe subject eveneens in het het team ##--tenant–<tenant-uuid>--## plaatsen.
Kan je in de WCM Admin een Server credential toevoegen met type Application identifier en de waarde ervan geef je de <moniker> op. Onderaan selecteer je bij app, de tenant <tenant-naam>.

Voor meer info/background zie hier: https://gpubp.antwerpen.be/#/wcmv4/content/api-authenticatie?id=content-bewerken-extra-stappen

dankjewel
<uw naam>
```

### Redactie configureren
Eenmaal de voorbereidingen van BRaaS rond zijn kan je bij de [tenant beheerder](/redactie/content/toegang-tenant-beheerder) rechten vragen voor deze afnemer. Volg hiervoor de volgende stappen:

1. Maak een rol aan
2. Gebruik deze rol voor je toepassing
3. Stel een workflow in

#### Maak een rol aan
Omdat je externe toepassingen wil beperken in vrijheid, wil je ze heel precies die rechten geven die ze nodig hebben **en niet meer**. Maak daarvoor een rol aan die overeenkomt met de naam van jouw toepassing, i.e. `<afnemer>_Rol` bijvoorbeeld `burgerportaal_Rol`.

Stel voor deze rol de rechten in zoals enkel lezen en schrijven van het `Nieuws` content type.

> Vergeet niet de rechten toe te kennen van de Content BSL (module) (deze staan bovenaan de rechtenlijst). 

#### Gebruik deze rol voor je toepassing 
De tenant beheerder kan jouw toepassing zoeken in de gebruikerslijst. Deze kan je terugvinden onder de naam `<afnemer applicatienaam>`. Merk op dat deze niet opgelijst worden, je kan ze enkel terugvinden d.m.v. een zoekopdracht in de gebruikerslijst.

Van hieruit kan de beheerder jouw toepassing `<afnemer applicatienaam>` aan een site toekennen en deze de rol `<afnemer>_Rol` geven die ervoor voorzien is.

#### Workflow maken en toekennen
Maak een specifieke workflow die je gaat gebruiken voor die content types die je wil manipuleren via de API, geef deze workflow de naam `<afnemer>_workflow`.

Stel de transities in en geef zeker de [nieuwe rol](/wcmv4/content/api-authenticatie?id=maak-een-rol-aan) die je hiervoor gebruikt ook de rechten om de transities te mogen uitvoeren. 

Zonder deze stap ga je een foutboodschap krijgen wanneer je content wil aanpassen:
 
```
"State transitions not allowed"
```


## Schema’s
Hier een schema van de voorbereiding en hoe die aan elkaar hangt:
### Via de API store (deprecated)
![API voorbereiding](../assets/api-prep-access.png 'De API voorbereiding (API store)')


### Via de Open Platform Marketplace
![API voorbereiding](../assets/api-prep-access-2.png 'De API voorbereiding (Open platform)')


### Flow bij content bewerken
![API calls](../assets/api-write-schema.png 'API calls om content te bewerken')

In bovenstaande afbeelding is de waarde van de `Application identifier`

* Open Programma = `Moniker`
* API store (deprecated) = `OrganisationId + AppId + VersionId`

?> Lees [hier hoe je een workflow inricht](/redactie/content/inrichten-workflows).

?> Lees hier meer over de [API calls om content te bewerken](/wcmv4/content/content-write).
