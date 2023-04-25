# Content via een view sorteren
Gebruik het [WCM Proxy endpoint](/wcmv4/content/endpoint-proxy).

Als je content wil sorteren gebruik je de volgende syntax: 

```shell
GET .../view?uuid=...&fields.order=[-]fieldname&lang=nl
```

> Momenteel kan je via de API slechts op één veld tegelijk sorteren.

*Haal alle content items op volgens de laatste-nieuws met de meest recentste bovenaan.*
```shell
GET .../view?uuid=42bb5422-74a4-4ed9-a9...1a8ee5040c&fields.order=-datum&lang=nl
```

!> TODO: hoe sorteren op meta data (bv lastModified)?