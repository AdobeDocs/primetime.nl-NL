---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
keywords: creatieve selectieregels;AdobeTVSDKConfig;ad creatieve prioriteiten;transformatieregels
title: Regels voor het bijwerken en creatieve selectie
exl-id: da0420a0-6be9-47c8-bdd8-45f0f1860f28
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Overzicht {#update-ad-creative-selection-rules-overview}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient bij een advertentieserver, bevat de VAST/VMAP-respons meestal meerdere advertentiefuncties ( `MediaFile` elementen), die elk een URL aan een verschillende container-codec versie verstrekken. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve objecten wilt opgeven, kunt u dit doen in het dialoogvenster [!DNL AdobeTVSDKConfig.json] configuratiebestand.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet behouden blijven [!DNL AdobeTVSDKConfig.json].
>* Dit bestand moet in het dialoogvenster [!DNL assets/] van uw project.
>* Het wijzigen van audiotracks tijdens het afspelen van advertenties verandert de audiotrack niet. Gebruikers mogen de audiotrack niet wijzigen wanneer een advertentie wordt afgespeeld.
>


U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioriteit* en *Normaliseren* regels.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

De regels voor Advertentie worden opgegeven met behulp van een JSON-bestand. De indeling van het JSON-bestand blijft in beide versies van de TVSDK hetzelfde. In TVSDK v3.0 moet het JSON-bestand met regels voor toevoegen echter worden gehost op een locatie die toegankelijk is via een HTTP-URL. De toepassing kan een instantie van AuditudeSettings gebruiken:

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
