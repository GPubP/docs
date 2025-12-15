# Toegangsbeheer

Deze pagina is bedoeld voor de ondersteunende teams die de toegang tot de redactie beheren.

## Stappen

Om een gebuiker toegang te geven tot een tenant in de redactie, dient deze de nodige autorisaties te krijgen in Keycloak. Keycloak rollen worden toegekend door het Integratie en Automatisatie team. Dankzij deze rollen kan de gebruiker aanmelden in de redactie-omgeving, en wordt de gevraagde tenant zichtbaar op de startpagina.

De rechten van de gebruiker binnen de tenant worden ingeregeld in BraaS. Zonder permissies in BraaS, kan het dus zijn dat een gebruiker een tenant kan zien op de landingspagina van de redactie, maar dat de tenant bij doorklikken niet geladen kan worden.

Om een gebruiker toe te voegen aan een tenant, diet deze in [BraaS](https://braas.antwerpen.be/teams) als lid toegevoegd worden aan het **tenant team** (via het menu "Teams" bovenaan). Dit team vind je door te zoeken op de **technische naam van de tenant** (die niet noodzakelijk dezelfde is als de display naam). De technische naam vind je in de [WCM Admin toepassing](https://wcm-admin.antwerpen.be/websites) onder "Websites" (websites zijn dus eigenlijk tenants in deze toepassing). Op de detailpagina van zo'n website zie je zowel de display naam als de technische naam. In de redactie zelf zie je enkel de display naam.

![WCM Admin](.//redactie/assets/wcm-admin-detail.png)

![Redactie](.//redactie/assets/redactie-landing.png)

Wanneer je in BraaS zoekt op de technische naam, zal je een team terugvinden met volgende omschrijving: "Tenant with name: <technical-name>". Je voegt vervolgens de gebruiker toe aan dit team.

![BraaS](.//redactie/assets/braas-tenant.png)

Verdere rechten binnen de tenant worden in de redactie zelf beheerd, door de tenant of site beheerder.

## Hoe maak ik iemand tenant beheerder?

