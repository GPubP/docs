# Content bewerken
Gebruik het [WCM Content Manager endpoint](/wcmv4/content/endpoint-content-manager) als je content wil schrijven. 

* Voorbereiding
* Create content item
* update content item


todo

Applicatie toegang afnemen/weigeren 
Indien de applicatie niet langer meer content mag beheren kan je één van volgende zaken doen:
de WCM Server Credentials disablen. (WCMv4)
het contract disablen op de API gateway (Kong)
de rol van deze specifieke user afnemen in de redactie (Redactie -> BRaaS)



Schema’s
Hier een schema van de voorbereiding en hoe die aan elkaar hangt:
Via de API store(deprecated)


Via de Open Platform Marketplace

Hier een schematisch overzicht van de effectieve call, authenticatie & autorisatie.


Application identifier = Moniker (Open program Marketplace)
Application identifier = OrganisationId + AppId + VersionId (API store = deprecated)

Content Types, blokken, etc
In sommige gevallen wil je meer weten over de opbouw van content types.
TODO: nog verder uitschrijven
