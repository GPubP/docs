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
        attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
      />
    </MapContainer>
  );
```

Aan de hand van bovenstaande code zul je een kaart zien met een focus op Antwerpen. Om elementen te renderen maken we gebruik van het `GeoJSON` format. Dit is een standaard formaat voor het uitwisselen van geografische data. Hier is een voorbeeld van hoe je dit kan doen:

Dit is 
```jsx
const geoJson = {
    type: "FeatureCollection",
    features: [
      {
        type: "Feature",
        properties: {
          type: "polygon",
          color: {
            label: "Red",
            value: "#ff0000",
          },
          area: 8748972.69,
          perimeter: 12767.42,
          name: "Veelhoek 1",
          fields: {
            label: {
              textType: "h2",
              text: "test",
            },
          },
        },
        geometry: {
          type: "Polygon",
          coordinates: [
            [
              [4.391487, 51.221978],
              [4.391487, 51.239822],
              [4.454673, 51.239822],
              [4.454673, 51.221978],
              [4.391487, 51.221978],
            ],
          ],
        },
        id: 249,
        style: {
          color: "#ff0000",
        },
      },
      {
        type: "Feature",
        properties: {
          type: "polygon",
          color: {
            label: "Red",
            value: "#ff0000",
          },
          area: 9455807.69,
          perimeter: 17417.38,
          name: "Veelhoek 2",
          fields: {
            label: {
              textType: "h2",
              text: "test",
            },
          },
        },
        geometry: {
          type: "Polygon",
          coordinates: [
            [
              [4.464288, 51.263459],
              [4.361268, 51.255295],
              [4.467379, 51.240036],
              [4.464288, 51.263459],
            ],
          ],
        },
        id: 312,
        style: {
          color: "#ff0000",
        },
      },
      {
        type: "Feature",
        properties: {
          type: "marker",
          color: {
            label: "Red",
            value: "#ff0000",
          },
          name: "Markering 3",
          fields: {
            label: {
              textType: "h2",
              text: "test",
            },
          },
        },
        geometry: {
          type: "Point",
          coordinates: [4.487983, 51.250352],
        },
        id: 332,
        style: {
          color: "#ff0000",
        },
      },
      {
        type: "Feature",
        properties: {
          type: "polyline",
          color: {
            label: "Red",
            value: "#ff0000",
          },
          length: 15618.29,
          name: "Polylijn 4",
          fields: {
            label: {
              textType: "h2",
              text: "test",
            },
          },
        },
        geometry: {
          type: "LineString",
          coordinates: [
            [4.37157, 51.270548],
            [4.348562, 51.212086],
            [4.476651, 51.21101],
          ],
        },
        id: 367,
        style: {
          color: "#ff0000",
        },
      },
    ],
  };
```

Om bovenstaande data te renderen op de kaart gebruiken we de `FeatureGroup` component van `react-leaflet`. 
We voegen dit component als volgt toe in de `MapContainer` en gebruiken de `useRef` hook om een referentie naar de `FeatureGroup` te krijgen.
```jsx
const geoData = useRef<FeatureGroup>(null);
return (
    <MapContainer
        center={position}
        zoom={13}
        scrollWheelZoom={false}
        style={{ height: "100vh", width: "100%" }}
    >
        <TileLayer
            attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
            url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        />
        <FeatureGroup ref={geoData} />
    </MapContainer>
); 
  );
```

In een useEffect hook kunnen we de data toevoegen aan de `FeatureGroup` component. In dit code voorbeeld zie je ook dat we de kleur van elke layer anders moeten mappen.
Dit is belangrijk, als je dit niet doet gaat de kleur niet doorkomen. 
( NOTE: Dit is enkel van toepassing als je geen marker of circle data hebt. )
```jsx
useEffect(()=> {
  const existingGeoData = new L.GeoJSON(geoJson, {});

    geoData?.current?.clearLayers();

    existingGeoData.eachLayer((layer: any) => {
      (layer.options as any).color = (layer as any).feature.style?.color;
      geoData.current?.addLayer(layer);
    });
}, []);
```
### Cirkels en Markers renderen 
Om Circles en Markers te renderen moeten we nog een stap toevoegen in onze useEffect hook. `react-leaflet` verwacht namelijk dat elke maker ern cirkel een unieke instantie zijn.
Door een nieuwe instantie van Marker of Circle aan te maken, zorg je ervoor dat elke Marker of Circle op de kaart afzonderlijk wordt behandeld en dat eventuele wijzigingen die je aanbrengt alleen van invloed zijn op die specifieke Marker of Circle.
Kortom, het aanmaken van een nieuwe instantie van Marker of Circle is essentieel voor de juiste werking van React Leaflet en om ervoor te zorgen dat je kaartcomponent correct wordt weergegeven en bijgewerkt.

```jsx
 const pointToLayer = (feature: any, latlng: any): Circle | Marker => {
    if (feature?.properties?.radius) {
        return L.circle(latlng, feature?.properties?.radius);
    }

    return L.marker(latlng);
};

const existingGeoData = new L.GeoJSON(geoJson, { pointToLayer });

geoData?.current?.clearLayers();

existingGeoData.eachLayer((layer: any) => {
    (layer.options as any).color = (layer as any).feature.style?.color;
    geoData.current?.addLayer(layer);
});
```
