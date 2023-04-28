# Update Content Item

Gebruik voor het aanpassen van content steeds het [ACPaaS WCM Content Manager endpoint](/wcmv4/content/endpoint-content-manager).

Een update van een content item doe je best in deze stappen:
  1. je haalt de data op via een [GET call](/wcmv4/content/content-write-update?id=get-content)
  2. [strip ongewenste data](/wcmv4/content/content-write-update?id=strip-ongewenste-data)
  3. pas de data aan waar nodig en gebruik dit als payload van de [PUT call](/wcmv4/content/content-write-update?id=put-content) 

## GET Content
```shell
'GET /acpaas/wcm-content-manager/v4/proxy/admin/content/v1/sites/{id}/content/{uuid}' \
--header 'apikey: <api-key>'
```

Je kan het volledige resultaat hiervan gebruiken als payload van de PUT call. Er zijn op ‘t eerste zicht heel wat berekende velden en id’s, het systeem kan hier weliswaar mee overweg.

## Strip ongewenste data
De volgende data haal je best uit de payload uit vooraleer je deze als basis gebruikt voor een update: 
* `meta.lastEditor`
* `meta.parents`
* …

## PUT Content
Gebruik de `PUT` operatie op de ACPaaS WCM Content Manager API zoals hieronder staat afgebeeld.
```shell
'PUT /wcm-content-manager/v4/proxy/admin/content/v1/sites/{id}/content/{uuid}/{status}' \
--header 'apikey: <api-key>' \
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

> In het pad geef je ook meteen de status mee. De mogelijkheden die je in de route hier kan gebruiken [staan hieronder](/wcmv4/content/content-write-update?id=status-verzetten).

De payload van je PUT call zal heel wat info bevatten, in de fields pas je de zaken aan die je wil veranderen.

## PATCH content
Momenteel wordt een PATCH nog niet ondersteund. Een PATCH is heel interessant om slechts één of een selectie van velden aan te passen met behoud van de rest van de data van een CI. Doordat nu enkel een PUT wordt ondersteund, worden CI’s steeds volledig vervangen. Op deze manier kan data die een redacteur in de Redactie aan een CI aangepast/toegevoegd heeft, verloren gaan wanneer dit CI via de API vervangen wordt door een PUT. 

Vooral in synchronisatie scenario’s worden bv elke nacht alle CI’s van een bepaalt Content Type geüpdated. Als we hierbij dus een PUT gebruiken, wordt alles vervangen en verliezen we dus de aanpassingen/verrijkingen van de redacteurs. 

De enige manier om dit vandaag op te lossen is:
1. haal het CI op via een [GET](/wcmv4/content/content-write-update?id=get-content) en gebruik dit als basis voor je nieuwe data
2. pas aan deze data enkel de velden aan met de laatste nieuwe gegevens van je extern bronsysteem
3. gebruik nu een [PUT](/wcmv4/content/content-write-update?id=put-content) call om het CI te vervangen.

## Status verzetten
Wanneer je de status van een content item wil verzetten zal je dit op 3 plaatsen moeten aangeven
1. in de `route`
2. het `meta.status` veld
3. het `meta.worfkflowState` veld

Voorbeeld PUT call

```shell
PUT /wcm-content-manager/v4/proxy/admin/content/v1/sites/{id}/content/{uuid}/published' \
--header 'apikey: <api-key>' \
--header 'Content-Type: application/json' \
--data-raw '<content payload>’
```

met payload:
```json
{
   "fields": {
       ...
  },
   "meta": {
       ...
        "status": "PUBLISHED",
        "workflowState": "gepubliceerd",
       ...
   },
}
```

Hanteer hiervoor deze waardes

| Route            | meta.status       | meta.workflowState                           |
|------------------|-------------------|----------------------------------------------|
| `draft`          | `DRAFT`           | `werkversie` of <alle eigen gemaakte states> |
| `pendingReview`  | `PENDING_REVIEW`  | `klaar-voor-nakijken`                        |
| `pendingPublish` | `PENDING_PUBLISH` | `klaar-voor-publicatie`                      |
| `scheduled`      | `SCHEDULED`       | N/A                                          |
| `published`      | `PUBLISHED`       | `gepubliceerd`                               |
| `unpublish` *    | `UNPUBLISHED`     | `gearchiveerd`                               |


> Let op deze schrijfwijze ! het is niet `unpublished`, maar `unpublish`.

> [!WARNING|label:Omslachtig]
> De huidige manier om content te maken en aan te passen is vrij omslachtig. We zijn ons ervan bewust en daarvoor is er een traject om dit te verbeteren in de WCMv5. 


## HTTP 403 ?
Ingeval je een `HTTP 403` krijgt bij het aanpassen van een Content Item is het mogelijk dat het content item **gelocked** is. Een lock wordt gelegd wanneer een redacteur het content item aan’t bewerken is vanuit de Redactie UI.
