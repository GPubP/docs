# GIS kaart

Laat toe om een GEO kaart te kiezen en hierop elementen te tekenen. 

> Zorg ervoor de de [GIS module](/modules/content/modules/module-gis) geactiveerd is.

## Voor content beheerders

Je kan 3 zaken configureren wanneer je een GIS kaart content component op je content type zet: 
- GIS basiskaarten
- Element kleuren
- Extra velden per element

### GIS basiskaarten
De GIS basiskaarten bepaalt wat de redacteur ziet wanneer hij/zij de GIS kaart content component bewerkt. 

Standaard is volgende basiskaart voorzien die de Vlaanderen in beeld brengt en specifiek Antwerpen daarboven in kleur zet:

[Vlaanderen als grijze achtergrond en Antwerpen in kleur](https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x})

```
https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x}
```  

Wil je de hele wereld in een grijze achtergrond dan kan je deze basiskaart configureren:
  
[De wereld als grijze achtergrond](https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x}) 
 
```
https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x}
```  

> [!info|label:Opmerking]
> Je kan verschillende basiskaarten als lagen op elkaar leggen. Wil je bijvoorbeeld zowel de wereld in't grijs en Antwerpen gekleurd daarboven dan gebruik je beide basiskaarten.

### Element kleuren

Als content beheerder kan je verschillende kleuren configureren. De redacteur kan per element dat hij/zij tekent de kleur kiezen.

Standaard hebben we volgende kleuren voorzien.

| Naam                        | HEX    |
|-----------------------------|--------|
| Afval en recyclage (petrol) | 007FA3 |
| Mobiliteit (grijs)          | 506D85 |
| Gezondheid (blauw)          | 0057B7 |
| Sporten en bewegen (groen)  | 007B5F |
| Kinderen en jeugd (paars)   | 8031A7 |
| Onderwijs (wijnrood)        | 840B55 |
| Cultuur (oranje)            | C05131 |
| Dienstverlening (stadsrood) | CF0039 |

### Extra velden per element

Als content beheerder kan je een [samengesteld content component](/common/content/concept-cc?id=standaard-samengesteld-en-custom). Dit component zal getoond worden aan de redacteurs waar zij de extra informatie kunnen invoeren per getekend element. 

> screenshot

## Voor redacteurs


## Voor ontwikkelaars

### Lege output

### Output met een gekozen link

## Voor bezoekers

