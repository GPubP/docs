# Assets tonen

## Assets configureren

Met de [Assets module](/modules/content/modules/module-assets) kunnen redacteurs ofwel

* Afbeeldingen kiezen en bewerken, via de [Afbeelding content component](/redactie/content/inrichten-cc-afbeelding)
* Bestanden opladen via de [Bestand content component](/redactie/content/inrichten-cc-bestand)

## Assets tonen

1. Via de [Content API](/wcmv4/content/content-item-read) haal je op welke afbeelding of welk bestand gebruikt werd op een [content item](/common/content/concept-ci). 
2. Haal hier de uuid op van de asset
3. Via de [Assets API](/wcmv4/content/assets) kan je afbeeldingen en bestanden downloaden. 

Hieronder zie je een voorbeeld payload wat je krijgt als je een content item ophaalt.

> [!Info|label:Performantie tip]
>
> We raden aan om **niet** te werken met de `original` afbeelding. Deze afbeelding is vaak te groot en niet geöptimaliseerd.
>
> Werk liever met de ge-cropte afbeelding, vooral als ze via de `begrensd` of `exact` [cropping methode zijn opgezet](/redactie/content/inrichten-cc-afbeelding?id=voor-contentbeheerders), die zorgt ervoor dat de gecropte versies ook verkleind worden waardoor er kleinere bestanden naar de afnemer z'n device gaan.



```json
{
   "_id": "60e5abd49cc9940009fbf124",
   "fields": {
        "afbeelding": {
            "meta": {
                "name": "Mijn afbeelding",
                "alt": "Mijn afbeelding",
                "title": "Mijn afbeelding",
                "description": "omschrijving",
                "copyright": "",
                "figuratively": true
            },
            "original": {
                "asset": {
                    "mime": "image/jpeg",
                    "uuid": "4ed0c27a-1b38-4718-9bce-7f0dadda48c5",
                    "size": {
                        "height": 1305,
                        "width": 2320
                    },
                    "fileName": "IMG_20210925_155306-2.jpg"
                }
            },
            "crops": {
                "small": {
                    "asset": {
                        "fileName": "IMG_20210925_155306-2.jpg",
                        "mime": "image/jpeg",
                        "size": {
                            "width": 1740,
                            "height": 1305
                        },
                        "uuid": "774522b9-31e2-4c05-b17f-faa183218963"
                    },
                    "cropValues": {
                        "x": 290,
                        "y": 0,
                        "width": 1740,
                        "height": 1305
                    },
                    "transformValues": {
                        "grayscale": false,
                        "blur": 0,
                        "rotate": 0
                    },
                    "renderValues": {
                        "zoomIn": {
                            "end": {
                                "y": 254.93784498645408,
                                "x": 520.4672897136303,
                                "height": 248.06215501354583,
                                "width": 660.3483609605128
                            },
                            "start": {
                                "width": 1339,
                                "height": 503,
                                "y": 0,
                                "x": 0
                            }
                        },
                        "focalPoint": {
                            "area": "center center"
                        }
                    },                    
                },
                "medium": {
                    "asset": {
                        "fileName": "IMG_20210925_155306-2.jpg",
                        "mime": "image/jpeg",
                        "size": {
                            "width": 2320,
                            "height": 1160
                        },
                        "uuid": "c03ac0fb-d9cd-4678-9f60-a1d72ed70903"
                    },
                    "cropValues": {
                        "x": 0,
                        "y": 73,
                        "width": 2320,
                        "height": 1160
                    },
                    "transformValues": {
                        "grayscale": false,
                        "blur": 0,
                        "rotate": 0
                    }
                },
                "large": {
                    ...
                },
                "extra-large": {
                    ...
                }
            }
        }
   },
   "meta": {
      ...
   },
   ...
}
```

## Zoom & Focuspunt

> Onderstaande werkt als de [tenant beheerder](/redactie/content/toegang-tenant-beheerder) de `Assets - Kenburns` of `Assets - Focalpoint` modules geactiveerd heeft voor je tenant. 

Een content beheerder kan kiezen om deze twee features aan te bieden aan de redacteur via de [Afbeelding content component](/redactie/content/inrichten-cc-afbeelding) configuratie. 





?> Lees meer over de [Assets Module](/modules/content/modules/module-assets).

?> Lees meer over de [Assets API](/wcmv4/content/assets).

!> beschrijf hoe je met de focus punt en zoom-in/uit overweg kan
!> beschrijf hoe je een bestand aanbiedt als download