# Datums, tijdstippen en tijd

Vermits de WCMv4 gebaseerd is op JSON, volgen we gedeeltelijk de regels, concreet: 

JSON specificatie voorziet dat datums, tijdstippen en tijden als string in de payload staan.

```json
"fields": {
   "een-tijdstip": "2022-10-03T08:00.000Z",  
   "een-datum": "2022-10-03",
   "een-tijd": "10:00"   
}
```


* Voor een **tijdstip**, volgen we de ISO8601 standaard, e.g. `2022-10-03T08:00.000Z`
* Voor een **datum**, volgen we de ISO8601 standaard, e.g. `2022-10-03`
* Voor tijd volgen we de standaard niet en komt de **tijd** uit de API als string zoals de redacteur deze ingevoerd heeft, e.g. `08:00`

Elastic App Search werkt op basis van RFC3339. 

?> [Zie hier voor het verband tussen RFC3339 en IS8601](https://ijmacd.github.io/rfc3339-iso8601/). 
 
Ze gebruiken deze spec enkel voor datums en tijdstippen, niet voor tijd. Dit betekent dat we de indexering in Elastic App Search als volgt vertalen: 

* Een tijdstip wordt geïndexeerd als 2022-10-03T08:00.000Z (zonder quotes) en past m.a.w. in een schema veld van het type date of text.
* Een datum wordt geïndexeerd als 2022-10-03 (zonder quotes) en past m.a.w. in een schema veld van het type date of text.
* Een tijd wordt geïndexeerd als ”08:00” (met quotes) en past m.a.w. enkel in een schema veld van het type text.

# Tijdzones
De API geeft alle **tijdstippen** terug [in UTC](https://en.wikipedia.org/wiki/ISO_8601#Coordinated_Universal_Time_(UTC)). Dit betekent dat je deze zelf nog moet omzetten in local time +2 of +1 afhankelijk van zomer of winteruur respectievelijk. 

Hou hier rekening mee als je resultaat [content lijsten gaat filteren](https://docs.google.com/document/d/1cMGpDkgqBnVhzlr7nr00YK8xciIESvIX1YmffqT6VzE/edit#heading=h.szigocerymr4) op datum.

Ingeval er enkel een **tijd** component is, komt deze tijd uit de API zoals de redacteur deze gekozen heeft. hier wordt geen omzetting van een local (BRU-tijdzone) naar UTC gedaan. Denk hierbij aan het tijdslot content component welke een output geeft als volgt: 

```json
"tijdslot": {
   "startDate": "2022-10-03",
   "startTime": "10:00",   
   "endTime": "12:00",
   "startDateTime": "2022-10-03T08:00.000Z", 
   "endDateTime": "2022-10-03T10:00.000Z"   
}
```

startTime is wel degelijk wat de redacteur gekozen heeft in de UI. Terwijl de startDateTime we de omzetting naar UTC maken. Het gevolg is dat je in dit scenario startDate en startTime samenvoegt dat je hier een local time krijgt en in essentie overeenkomt met `2022-10-03T10:00+02:00`. 
