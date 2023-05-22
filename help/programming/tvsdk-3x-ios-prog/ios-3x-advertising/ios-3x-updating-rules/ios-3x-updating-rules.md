---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
keywords: creatieve selectieregels;AdobeTVSDKConfig;ad creatieve prioriteiten;transformatieregels
title: Regels voor het bijwerken en creatieve selectie
exl-id: e364a033-7244-4de6-8505-91fb3e56959d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Overzicht {#update-ad-creative-selection-rules-overview}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient bij een advertentieserver, bevat de VAST/VMAP-respons meestal meerdere advertentiefuncties ( `MediaFile` elementen), die elk een URL aan een verschillende container-codec versie verstrekken. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve objecten wilt opgeven, kunt u dit doen in het dialoogvenster [!DNL AdobeTVSDKConfig.json] configuratiebestand.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet behouden blijven [!DNL AdobeTVSDKConfig.json].
>* U kunt dit bestand op een willekeurige locatie plaatsen die toegankelijk is voor uw bundel.
>


U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioriteit* en *Normaliseren* regels.

**[!UICONTROL Disabling Pre-Roll]**

Om pre-rol onbruikbaar te maken zult u de standaardopportuniteitsgenerators moeten veranderen om niet de pre-rolvraag te maken. Standaard gebruikt TVSDK de volgende opportuniteitsgeneratoren:

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    result.push(new AdSignalingModeOpportunityGenerator()); 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
} 
```

Om pre-rol op levende stromen onbruikbaar te maken, zou dit moeten veranderen om slechts SpliceOutOpportunityGenerator te omvatten:

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    if (preroll_enabled == true) { 
        result.push(new AdSignalingModeOpportunityGenerator()); 
    } 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
}
```
