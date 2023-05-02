# Taxonomy API

## Voorbereiding
Om taxonomieën te beheren moet je dezelfde voorbereiding uitvoeren als voor het beheren van content. Zorg dat je [alle stappen hebt doorlopen](/wcmv4/content/api-authenticatie?id=content-bewerken-extra-stappen). 

Taxonomieën situeren zich op **tenant niveau**. Via de API werken met taxonomieën vergt een extra recht. Zorg ervoor dat de toepassing die in de gebruikerslijst staat van de Redactie de rol **Contentbeheerder** krijgt op tenant niveau.

> [!info|label:Definities]
> * Een `taxonomie` is de boom of de container waarin termen opgenomen zijn, bv thema, district, doelgroep, etc.
> * Een taxonomy heeft één of meerdere `termen` die
>   * in een **hiërarchie** staan
>   * een **volgorde** kennen 
>   * een `label` hebben dat kan voorkomen in verschillende talen
>   * een `externe referentie` kunnen bevatten, vooral handig als de master van die taxonomie data uit een ander systeem komt (e.g. Salesforce)
