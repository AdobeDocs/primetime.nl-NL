---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
seo-title: Regels voor het bijwerken en creatief selecteren
title: Regels voor het bijwerken en creatief selecteren
uuid: 84cc13d1-21a3-456b-95c8-200bfec7b453
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Overzicht {#updating-ad-creative-selection-rules-overview}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient aan een advertentieserver, omvat de reactie VAST/VMAP gewoonlijk veelvoudige ad creatieve ( `MediaFile` elementen), elk waarvan een URL aan een verschillende container-codec versie verstrekt. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve toevoegingen wilt specificeren, kunt u dit in het [!DNL AdobeTVSDKConfig.json] configuratiedossier doen.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet achterblijven [!DNL AdobeTVSDKConfig.json].
>* Dit bestand moet in de [!DNL assets/] map van uw project worden geplaatst.
>



U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioritaire* regels en *Normaliseer* regels.

## Pre-Roll uitschakelen {#disabling-preroll}

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

