# Renderen via leaflet

Als redacteurs werken met een [GIS kaart](/redactie/content/inrichten-cc-gis-kaart) in de redactie geven we je hier enkele tips om hier in de frontend mee om te gaan.

## Render de kaart

!> TODO: beschrijf hoe je via leaflet GIS data kan tonen (zowel de kaart als de referentie)

Als je de kaart presenteert kan je gebruik maken van de `mapControls` informatie die je op het content item terug vindt.
Specifiek kan je de **positie** van de kaart zetten op basis van de `latlng` waardes uit het content item.
Daarnaast kan je de kaart **inzoomen** volgens de `zoom` waarde uit het content item.

```json
{
    "_id": "659d60edae970038264276cc",
    "uuid": "dac8e1ce-8b6c-437a-9191-c8981ba19a28",
    "fields": {
        "gis-kaart": {
            "mapControls": {
                "latLng": {
                    "lat": 51.23462231776156,
                    "lng": 4.424743652343751
                },
                "zoom": 13
            },
            "mapData": { ... }
        }
    }
}
```

## Render de elementen op de kaart

Om elementen te kunnen renderen op de kaart hebben we eerste onze kaart nodig. Deze kan je ophalen via de `mapData` informatie op het content item.
In React kan je gebruik maken van "react-leaflet" om de kaart te renderen. Hier is een voorbeeld van hoe je dit kan doen:

```jsx
const [position, setPosition] = useState<[number, number]>([
    51.26084065010475, 4.509208771036742,
]);
  return (
    <MapContainer center={position} zoom={13} scrollWheelZoom={false} style={{ height: "100vh", width: "100%" }}>
        <TileLayer
            url="https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x}"
            key="first"
        />
        <TileLayer
            url="https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x}"
            key="last"
        />
    </MapContainer>
  );
```

Aan de hand van bovenstaande code zul je een kaart zien met een focus op Antwerpen. Om elementen te renderen maken we gebruik van het `GeoJSON` format. Dit is een standaard formaat voor het uitwisselen van geografische data. Hier is een voorbeeld van hoe je dit kan doen:

Om bovenstaande data te renderen op de kaart gebruiken we de `FeatureGroup` component van `react-leaflet`.
We voegen dit component als volgt toe in de `MapContainer` en gebruiken de `useRef` hook om een referentie naar de `FeatureGroup` te krijgen.

```tsx
const yourMapComponent: FC<mapComponentType> = (mapData) => {
const geoData = useRef<FeatureGroup>(null);
return (
    <MapContainer
        center={mapData.mapControls.properties.latLng}
        zoom={mapData.mapControls.properties.zoom}
        style={{ height: "100vh", width: "100%" }}
    >
        <TileLayer
            url="https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x}"
            key="first"
        />
        <TileLayer
            url="https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x}"
            key="last"
        />
        <FeatureGroup ref={geoData} />
    </MapContainer>
);
}
```

### Cirkels en Markers en kleuren renderen

In een useEffect hook kunnen we de data toevoegen aan de `FeatureGroup` component. In dit code voorbeeld zie je ook dat we de kleur van elke layer anders moeten mappen.
Dit is belangrijk, als je dit niet doet gaat de kleur niet doorkomen.

Om Circles en Markers te renderen moeten we nog een stap toevoegen in onze useEffect hook. `react-leaflet` verwacht namelijk dat elke marker en cirkel een unieke instantie zijn.
Door een nieuwe instantie van Marker of Circle aan te maken, zorg je ervoor dat elke Marker of Circle op de kaart afzonderlijk wordt behandeld en dat eventuele wijzigingen die je aanbrengt alleen van invloed zijn op die specifieke Marker of Circle.
Kortom, het aanmaken van een nieuwe instantie van Marker of Circle is essentieel voor de juiste werking van React Leaflet en om ervoor te zorgen dat je kaartcomponent correct wordt weergegeven en bijgewerkt.

```tsx
useEffect(()=> {
    // in deze pointToLayer functie maken we telkens een niewe instantie van Marker of Circle aan
    const pointToLayer = (feature: any, latlng: any): Circle | Marker => {
        if (feature?.properties?.radius) {
            return L.circle(latlng, feature?.properties?.radius);
        }

        return L.marker(latlng);
    };
    
    // we maken een nieuwe GeoJSON aan met de data van de kaart
    const geoJsonData = new L.GeoJSON(clone(mapData.mapData.properties), { pointToLayer });

    // we verwijderen de oude data
    geoData?.current?.clearLayers();
    
    // we voegen de nieuwe data toe
    geoJsonData.eachLayer((layer) => {
        (layer.options as any).color =
            (layer as any).feature.style?.color ||
            (layer as any).feature.properties?.color?.value ||
            DEFAULT_COLOR.value;
        geoRef.current?.addLayer(layer);
    })
}, []);
```

### Het complete component

Hier is het complete component dat je kan gebruiken om de data te renderen op de kaart:

```tsx
import React, { FC, useEffect, useRef } from "react";
import { FeatureGroup, MapContainer, TileLayer } from "react-leaflet";
import L from "leaflet";
import { clone } from "ramda";

const yourMapComponent: FC<mapComponentType> = (mapData) => {
    const geoData = useRef<FeatureGroup>(null);

    useEffect(() => {
        const pointToLayer = (feature: any, latlng: any): Circle | Marker => {
            if (feature?.properties?.radius) {
                return L.circle(latlng, feature?.properties?.radius);
            }

            return L.marker(latlng);
        };

        const geoJsonData = new L.GeoJSON(clone(mapData.mapData.properties), { pointToLayer });

        geoData?.current?.clearLayers();

        geoJsonData.eachLayer((layer) => {
            (layer.options as any).color =
                (layer as any).feature.style?.color ||
                (layer as any).feature.properties?.color?.value ||
                DEFAULT_COLOR.value;
            geoData.current?.addLayer(layer);
        });
    }, []);

    return (
        <MapContainer
            center={mapData.mapControls.properties.latLng}
            zoom={mapData.mapControls.properties.zoom}
            style={{ height: "100vh", width: "100%" }}
        >
            <TileLayer
                url="https://services.arcgisonline.com/ArcGIS/rest/services/Canvas/World_Light_Gray_Base/MapServer/tile/{z}/{y}/{x}"
                key="first"
            />
            <TileLayer
                url="https://tiles.arcgis.com/tiles/1KSVSmnHT2Lw9ea6/arcgis/rest/services/basemap_stadsplan_v6/MapServer/tile/{z}/{y}/{x}"
                key="last"
            />
            <FeatureGroup ref={geoData} />
        </MapContainer>
    );
};
```
