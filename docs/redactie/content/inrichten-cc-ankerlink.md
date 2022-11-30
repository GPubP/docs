# Ankerlink
Wordt typisch gebruikt om bovenaan een pagina een reeks (anker)linken te voorzien die je naar lager gelegen gedeeltes van de pagina brengen.

Geeft de mogelijkheid om een reeks ankerlinken op te geven naar eerder gedefinieerde ankerplaatsen.

Het idee is dat je eerst ankerplaatsen aanlegt. Momenteel is de enigste manier om deze aan te leggen door gebruik te maken van [tekstlijnen](/redactie/content/cc/tekstlijn-cc.md). 

# Voor contentbeheerders
Er zijn in eerste instantie geen configuratie opties voor de contentbeheerder. 
Gewoonlijk worden er wel in de basisinstellingen voor deze component, gekozen om meerdere ankerlinken toe te laten (multiple).

# Voor redacteurs
Eerst zorg je dat er content is gemaakt obv tekstlijnen die als ankerplaats dienen. Vanaf dan, kan je deze tekstlijnen kiezen in de dropdown voor je nieuwe ankerlink. Standaard wordt de inhoud van de tekstlijn overgenomen als label van de nieuwe ankerlink, maar je kan deze overschrijven naar wens.

![Ankerlink configuratie](../assets/ankerlink-config.gif)

([Bekijk dit op YouTube](https://youtu.be/zYJEdosNSVA ':target="_blank"'))

# Voor ontwikkelaars
## Lege output
```json
{
   "_id": "616056f8ce65be000a546530",
   "fields": {
       "ankerlinken": []
   },
   "meta": {
      ...
   },
   ...
}
```

## Output met ankerlinken
```json
{
   "_id": "616056f8ce65be000a546530",
   "fields": {
       "rubrieken": [
           {
               "multiple": false,
               "semanticType": "tekstlijn",
               "fieldType": "e74764ac-48ff-4b04-a199-d89e6f8bd266",
               "fieldRef": "aea73051-6f4b-47c6-9e8f-f8dbb8605a74",
               "type": "textWithStyle",
               "uuid": "042275b3-26fe-4409-98db-e96870259b1e",
               "value": {
                   "text": "titel 1",
                   "textType": "div"
               }
           },
           {
               "multiple": false,
               "semanticType": "tekstlijn",
               "fieldType": "e74764ac-48ff-4b04-a199-d89e6f8bd266",
               "fieldRef": "aea73051-6f4b-47c6-9e8f-f8dbb8605a74",
               "type": "textWithStyle",
               "uuid": "54f7e33f-5eab-49c0-903e-d0e13624af2f",
               "value": {
                   "text": "nog een titel",
                   "textType": "div"
               }
           }
       ],
       "ankerlinken": [
           {
               "value": {
                   "label": "titel 1",
                   "link": "/rubrieken/uuid/042275b3-26fe-4409-98db-e96870259b1e"
               },
               "uuid": "7f79311c-06e6-4ea6-8c0b-4bfda45c0447"
           },
           {
               "value": {
                   "label": "nog een titel",
                   "link": "/rubrieken/uuid/54f7e33f-5eab-49c0-903e-d0e13624af2f"
               },
               "uuid": "5ccf315b-049d-4786-8052-826a5868a3dd"
           }
       ]
   },
   "meta": {
      ...
   }, 
   ...
}
```

?> Ga terug naar het [overzicht van alle content componenten](/redactie/content/inrichten-cc-standaard.md)