# Werken met paragrafen

Een [paragraaf](/redactie/content/inrichten-cc-paragraaf) is een veld type dat gebruikt kan worden op een content type. Het laat toe om de redacteur een keuze te bieden van wat hij/zij net wil toevoegen van content. Zo kan je bijvoorbeeld de redacteur laten kiezen tussen een tekstlijn, een nummer, een datum, etc, of zelfs [custom content componenten](/redactie/content/inrichten-cc?id=custom-content-componenten). Hier zie je een voorbeeld hoe de redacteur uit 4 mogelijke acties kan kiezen bij het aanmaken van een service pagina:

![Paragraaf](../assets/gpubp-paragraphs.jpg 'Kies een paragraaf')


Dit betekent dat het niet vastligt welke structuur er gaat uitkomen voor een het opbouwen van service pagina in de user interface. Vandaar dat de ([WCM Proxy](/wcmv4/content/endpoint-proxy)) API op dit vlak extra informatie gaat voorzien die je kan gebruiken in de frontend.  

*Stel je haalt een servicepagina auto-inbraak op:*
```shell
GET /wcm-proxy/v4/content/v1/sites/{id}/content?slug=auto-inbraak&lang=nl

```

De redacteur had voor de `auto-inbraak` 3 acties opgezet welke je terug zal vinden in de `acties` array waar elk element overeenkomt met één paragraaf: 
```json
  ...
       "acties": [
           {
               "uuid": "8adec0f2-fee5-408d-a007-e3eea98d44ba",
               "fieldType": "07d930ac-6094-45de-a53d-c57f4dd0fdb6",
               "type": "fieldgroup",
               "multiple": false,
               "fieldRef": "d29e425e-4ebf-4a69-a0f1-516706efc312",
               "componentType": "service-afspraak",
               "semanticName": "afspraak",
               "preset": "85633ab0-3b6b-43f3-9af8-9a371e0235fa"
               "value": { ... }
           },
           {
               "uuid": "09b7166a-abec-4354-96a2-d2888bfb494a",
               "fieldType": "07d930ac-6094-45de-a53d-c57f4dd0fdb6",
               "type": "fieldgroup",
               "multiple": false,
               "fieldRef": "ecd91fd1-023a-4cb1-a9ea-fd08686457a0",
               "componentType": "service-doorverwijzing",
               "semanticName": "eerste-doorverwijzing",
               "preset": "c4d37892-9899-461d-8d9d-93ceab12ed0a",
               "value": { ... }
           },
           {
               "uuid": "ce950dfd-fae5-48b0-859d-aec2264270f2",
               "fieldType": "07d930ac-6094-45de-a53d-c57f4dd0fdb6",
               "type": "fieldgroup",
               "multiple": false
               "fieldRef": "ecd91fd1-023a-4cb1-a9ea-fd08686457a0",
               "componentType": "service-doorverwijzing",
               "semanticName": "tweede-doorverwijzing",
               "preset": "c4d37892-9899-461d-8d9d-93ceab12ed0a",
               "value": { ... }
           }
       ]
```


Het belangrijkste dat je hierboven zal zien is het volgende:
* **componentType** (`service-afspraak` of `service-doorverwijzing`) geeft aan welk custom content component de redacteur heeft gekozen.
* **componentName** (`afspraak`) is de systeemnaam van het component binnen deze paragraaf
* ~~**semanticType**~~ deprecated (is nu `semanticName` geworden) geeft de naam van het veld terug dat de content beheerder heeft voorzien
* **value** is de inhoud van de paragraaf

Daarnaast
* **preset** is de uuid van het custom content component definitie
* **type** (`fieldgroup`) dit geeft aan dat de redacteur een paragraaf heeft toegevoegd op basis van een custom content component. 
* **multiple** geeft aan of de redacteur meerdere items kan ingeven voor z’n gekozen paragraaf (true|false)

*Ingeval de redacteur geen custom content component zou toegevoegd hebben maar een standard content component zoals een tekstlijn* 
```json  
  ...
       "acties": [
           {
               "uuid": "b2e20ac5-3abc-48db-a722-91c0b0c772be",
               "type": "textWithStyle",
               "fieldRef": "8860975a-cc70-4b2c-8e3f-17d1bcadb489",
               "fieldType": "e74764ac-48ff-4b04-a199-d89e6f8bd266",
               "componentType": "tekstlijn",
               "semanticName": "sub-titel",
               "multiple": false
               "value": { ... }
            }
       ]
```

Hier zie je dat 
* **componentType** (`tekstlijn`) het veld type aangeeft dat de redacteur heeft toegevoegd als paragraaf. (in c komt dit overeen met `type`, maar is in `componentType` de meer leesbare versie genoteerd)
* **componentName** is de systeemnaam van het component binnen deze paragraaf
* ~~**semanticType**~~ deprecated (is nu `semanticName` geworden) geeft de naam van het veld terug dat de content beheerder heeft voorzien
* **preset** is afwezig