# Video embed
Geef een url van een videofragment. Dit werkt heel gelijkaardig zoals een [audio embed](/redactie/content/inrichten-cc-audio-embed.md) component.

# Voor contentbeheerders
De enige configuratie optie is om aan te geven aan de frontend dat een videofragment automatisch mag afgespeeld worden.

![Video embed configuratie](../assets/video-embed-config.png)

# Voor redacteurs
Een redacteur kan eenvoudigweg een videolink plakken in het voorziene vak en er komt een preview zodat de redacteur kan zien / horen of de juiste link geplakt is.

![Video embed redactie](../assets/video-embed-redactie.png)

# Voor ontwikkelaars

## Output met autostart van videofragment

```json
{
    "_id": "639b2607f07ca50007092544",
    "fields": {
        "test-video-embed": {
            "opties": [
                "autoplay"
            ],
            "video": "https://www.youtube.com/embed/GwoYSWYDC0E"
        },
    "uuid": "2e038d59-aa5b-4744-8b36-dd3823347396",
    ...
}
```

?> Ga terug naar het [overzicht van alle content componenten](/redactie/content/inrichten-cc-standaard.md)






























