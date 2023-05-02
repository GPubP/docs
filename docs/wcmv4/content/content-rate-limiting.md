# Rate limiting

Alle requesten naar de WCM API gaan over de API Gateway van Digipolis. Deze heeft een nieuwe beveiliging tegen o.a. DDOS attacks, namelijk: Rate Limiting. 

De gateway laat een aantal requesten door per minuut, van zodra je erover zit zal de gateway alle volgende requesten binnen die minuut blokkeren. 

Als afnemer ga je op dat moment een `HTTP 429` krijgen. Idealiter geef je de bezoeker een gepaste boodschap hiervoor terug.

Wil je meer weten over rate limiting, bekijk dan hier de ACPaaS documentatie: https://wiki.antwerpen.be/ACPAAS/index.php?title=Rate_Limiting&sfr=ACPAAS&title=Rate_Limiting 
