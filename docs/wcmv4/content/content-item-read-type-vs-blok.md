# Content types vs Content blokken
Wanneer het content item dat je ophaalt, gemaakt is obv een content type zal dit de output lichtjes veranderen dan wanneer het gemaakt is obv een content blok.

Ingeval het gemaakt is van een content type krijg je:

```json
{
  ...
  "meta": {
    "slug": {
       "nl": "kantoor-noorderlaan”
    },
    "label": "Kantoor Noorderlaan",
    "contenttype": "kantoor",
    ... 
  },
}
```

Ingeval het gemaakt is van een content blok krijg je:

```json
{
  ...
  "meta": {
    "slug": {},
    "label": "Kantoor Noorderlaan",
    "contenttype": "kantoor",
    ... 
  },
}
```


Het verschil is in `meta.slug` wat wel (content type) of niet (content blok) opgevuld gaat zijn. 

> PS1: je zou verwachten dat de property `meta.contenttype` ook zou veranderen naar bv `meta.contentblok`, maar dit is niet het geval.
> PS2: ingeval je een conversie van een content type naar een content blok hebt laten uitvoeren zullen oude content items nog steeds hun slug behouden.
