---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
title: Regels voor het bijwerken en creatief selecteren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Overzicht {#updating-ad-creative-selection-rules}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient bij een advertentieserver, bevat de VAST/VMAP-respons meestal meerdere advertentiefuncties ( `MediaFile` elementen), die elk een URL aan een verschillende container-codec versie verstrekken. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve objecten wilt opgeven, kunt u dit doen in het dialoogvenster [!DNL AdobeTVSDKConfig.json] configuratiebestand.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet behouden blijven [!DNL AdobeTVSDKConfig.json].
>* Dit bestand moet worden gehost op het CDN (Content Delivery Network).
>

U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioriteit* regels en *Normaliseren* regels.
