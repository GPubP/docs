# Geo rendering

Met de [GIS module](/modules/content/modules/module-gis) kunnen redacteurs ofwel

* GIS punten kiezen, via de [GIS referentie content component](/redactie/content/inrichten-cc-gis-referentie)
* kaarten aanmaken en bewerken via de [GIS kaart content component](/redactie/content/inrichten-cc-gis-kaart)

## Werken met GEO data van de GIS kaart

Een redacteur kan een content item maken waar hij/zij op een een GIS kaart elementen tekent zoals lijnen en polygonen. Vraag is, wat doen we met die extra data?
Er zijn typisch 2 manieren om hiermee overweg te gaan:

1. de frontend haalt het content item op en [rendert deze op een leaflet](/frontend/content/geo-rendering-leaflet) kaart.
2. er wordt een routine gemaakt die deze data oppikt en [gaat bewaren op de GIS server](/frontend/content/geo-rendering-gisserver).
