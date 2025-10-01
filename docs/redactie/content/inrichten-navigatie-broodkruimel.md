# Broodkruimel

De broodkruimel wordt volledig opgebouwd in de frontend maar in het sitestructuur compartiment vind je een hint naar de structuur indien je deze opbouwt op basis van de [site structuur](/redactie/content/inrichten-navigatie-broodkruimel) :

![Sitestructuur op content item instellen](../assets/navigatie-ci-sitestructuur.png 'Sitestructuur op content item instellen')

De redactie voorziet een eenvoudige call om het broodkruimelpad op te bouwen op basis van de ingerichte sitestructuur : 

```shell
GET .../navigations/v1/sites/{siteId}/content/{contentId}/breadcrumbs
```
Meer informatie over dit API endpoint vind je [hier](/wcmv4/content/navigation-breadcrumb)
