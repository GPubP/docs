# Content blokken

[Content types](/common/content/concept-ct) en content blokken liggen heel dicht bij elkaar, ze delen quasi 99% van de eigenschappen met elkaar. Beide zijn sjablonen voor het maken van content items. Het subtiele verschil is:

Content items gemaakt obv een ...

| Content Type                                                    | Content Blok                                                      |
|:----------------------------------------------------------------|:------------------------------------------------------------------|
| ...worden gebruikt voor **een volledige pagina** in de frontend | ...worden gebruikt voor een **deel van de pagina** in de frontend |
| ...hebben link waardoor je in de frontend er naar kan navigeren | ...hebben geen link, je kan er niet naar navigeren.               |
| ...kunnen gebruikt worden in een menu                           | ...kunnen **niet** gebruikt worden in menu                        |
| ...kunnen een plaats hebben in de sitestructuur                 | ...hebben **geen** plaats in de sitestructuur                     |

Er zijn een 2 typische use cases waarvoor je content blokken gaat inzetten:

1. je wil een stuk content opmaken dat op verschillende plekken kan hergebruikt worden
2. je wil content aanmaken dat op zich geen eigen detailpagina heeft, maar eerder voorkomt in een opsomming/lijst van een andere pagina. 
   bv. in een help pagina tonen we FAQ items wat bestaat uit een vraag en antwoord. Het is voldoende om deze in een lijst op de hulp pagina te tonen, er moet niet naar een individueel FAQ item gesurft kunnen worden.
