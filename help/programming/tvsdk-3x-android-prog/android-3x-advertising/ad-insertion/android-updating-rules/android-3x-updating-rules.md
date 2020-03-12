---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
seo-title: Regels voor het bijwerken en creatieve selectie
title: Regels voor het bijwerken en creatieve selectie
uuid: 77d8e186-01b5-4d62-8686-28f431d18876
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# Overzicht {#update-ad-creative-selection-rules-overview}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient aan een advertentieserver, omvat de reactie VAST/VMAP gewoonlijk veelvoudige ad creatieve ( `MediaFile` elementen), elk waarvan een URL aan een verschillende container-codec versie verstrekt. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve toevoegingen wilt specificeren, kunt u dit in het [!DNL AdobeTVSDKConfig.json] configuratiedossier doen.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet achterblijven [!DNL AdobeTVSDKConfig.json].
>* Dit bestand moet in de [!DNL assets/] map van uw project worden geplaatst.
>* Het wijzigen van audiotracks tijdens het afspelen van advertenties verandert de audiotrack niet. Gebruikers mogen de audiotrack niet wijzigen wanneer een advertentie wordt afgespeeld.
>



U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioritaire* regels en *Normaliseer* regels.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

De regels voor Advertentie worden opgegeven met behulp van een JSON-bestand. De indeling van het JSON-bestand blijft in beide versies van de TVSDK hetzelfde. In TVSDK v3.0 moet het JSON-bestand met regels voor toevoegen echter worden gehost op een locatie die toegankelijk is via een HTTP-URL. De toepassing kan een instantie van AuditudeSettings gebruiken:

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
