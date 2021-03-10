---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
keywords: creatieve selectieregels;AdobeTVSDKConfig;ad creatieve prioriteiten;transformatieregels
title: Regels voor het bijwerken en creatieve selectie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Overzicht {#update-ad-creative-selection-rules-overview}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient aan een advertentieserver, omvat de reactie VAST/VMAP gewoonlijk veelvoudige ad creatieve ( `MediaFile` elementen), elk waarvan een URL aan een verschillende container-codec versie verstrekt. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve toevoegingen wilt specificeren, kunt u dit in het [!DNL AdobeTVSDKConfig.json] configuratiedossier doen.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet [!DNL AdobeTVSDKConfig.json] blijven.
>* Dit bestand moet in de map [!DNL assets/] van uw project worden geplaatst.
>* Het wijzigen van audiotracks tijdens het afspelen van advertenties verandert de audiotrack niet. Gebruikers mogen de audiotrack niet wijzigen wanneer een advertentie wordt afgespeeld.

>



U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioriteitsregels* en *Normaliseren* regels.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

De regels voor Advertentie worden opgegeven met behulp van een JSON-bestand. De indeling van het JSON-bestand blijft in beide versies van de TVSDK hetzelfde. In TVSDK v2.5 moet het JSON-bestand met regels voor toevoegen echter worden gehost op een locatie die toegankelijk is via een HTTP-URL. De toepassing kan een instantie van AuditudeSettings gebruiken:

```
//TVSDK v2.5 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```

