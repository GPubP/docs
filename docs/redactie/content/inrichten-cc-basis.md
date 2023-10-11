# Content componenten

## Basis eigenschappen
Alle componenten hebben 4 basiseigenschappen:
1. Meerdere
2. Verplicht
3. Vertaalbaar
4. Verborgen	

### Meerdere (multiple)
Dit geeft aan of de redacteur van een gegeven component er één of meerdere kan invoeren. bv. je laat toe dat de redacteur tot 3 content referenties kan invoeren voor een content item. 

Standaard staat meerdere/multiple uit en kan er slechts één ding ingegeven worden.

![GPubP high level](..//redactie/assets/GPubP-cc-meerdere.jpg)

Voor ontwikkelaars zal het verschil merkbaar zijn of de content al dan niet in een array gewrapped zal worden.

### Verplicht
Duid aan dat dit content component verplicht moet ingevuld worden door de redacteur. Een content beheerder kan deze validatie optie vinden in de validatie tab van het content component.

![GPubP high level](..//redactie/assets/GPubP-cc-verplicht.jpg)

### Vertaalbaar
todo

### Verborgen
Dit content component zit wel in het content type/blok/custom component, maar is niet zichtbaar voor de redacteur. 

Meestal wordt dit gecombineerd met een standaard waarde en gebruik je dit om dit mee te geven aan de frontend zonder dat de redacteur hierover lastig gevallen moet worden. 

![GPubP high level](..//redactie/assets/GPubP-cc-verborgen.jpg)

## Start content componenten

### Voor content types
Elk content type zal out of the box starten met 4 content componenten:
1. Titel - Standaard Titel
2. Teaser - Standaard tekstvak
3. Meta tags - Meta
4. Open graph protocol - Og 

De standaard titel (1) en standaard tekstvak (2) zijn speciale systeem componenten die een content beheerder niet kan kiezen. Ze worden gebruikt om de titel en de teaser te herkennen van alle content types. Het gedrag ervan is gelijkaardig aan een tekstlijn en tekstvak respectievelijk.

### Voor content blokken
Elke content blok start enkel met
1. Titel - Standaard Titel

De standaard titel (1) is een speciaal systeem componenten die een content beheerder niet kan kiezen. Het wordt gebruikt om de titel te herkennen van alle content blokken. Het gedrag ervan is gelijkaardig aan een tekstlijn.