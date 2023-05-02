# Search inrichten

Als content en site beheerder zal je vaak een search inrichting moeten uitvoeren. Dit houdt het volgend in: 

1. Content opnemen in een index
2. Een zoekervaring configureren

## Voorbereiding

> Zorg ervoor dat de [Search module](/modules/content/modules/module-search) is geactiveerd voor je tenant en dat de **Search feature** voor je site is aangezet. (Site > instellingen > Elastic App Search)

![Search feature](../assets/search-feature-site.jpg 'Zet de search feature aan op site niveau')


## Indexen opzetten

Je kan één of meerdere indexen aanmaken. Elke index hier komt overeen met een aparte engine in Elastic App Search, meer nog, als de site [meertalig](/redactie/content/inrichten-meertaligheid) is ingericht zal elke **index hier overeenkomen met één engine per taal**.


> [!info|label:Hoeveel index maak je best]
> Je kan kiezen om één index te maken waar alle content samen zit of meerdere indexen met elks een deel van de content. Wat is het beste? Wel, dit hangt af van: 
> * **Search relevantie tuning:** je wil gewichten en boosts anders inrichten 
> * **Synoniemen:** de situatie vereist andere synoniemen, zo is `bank` iets heel anders in een recreatieve context of een financiële context.
> * **Curations:** Je wil voor specifieke zoektermen, andere pagina's vastpinnen bovenaan de zoekresultaten
> 
> In essentie maak je een nieuwe index als je voor één van deze redenen wil afwijken van reeds bestaande indexen. 

!> todo: verder toelichten hoe je een index kan inrichten en de rol van search mappers (+ custom mappers?)

## Een zoekervaring configureren

!> todo: vertel over de zoekindex ref en zoekindex veld ref component alsook een verwijzing naar het analyse doc 

?> Achtergrond info: https://wiki.antwerpen.be/itvanatotz/index.php/Elastic_App_Search#Toegang_tot_de_App_Search_toepassing

