---
description: U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.
title: Regels voor het bijwerken en creatief selecteren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Overzicht {#updating-ad-creative-selection-rules}

U kunt het configuratiebestand van TVSDK (AdobeTVSDKConfig.json) gebruiken om de prioriteiten voor een creatieve selectie op VAST/VMAP-reacties bij te werken. U kunt dit configuratiebestand ook gebruiken om de URL-omzettingsregels voor de bron van advertenties te definiëren.

Wanneer uw videospeler een verzoek indient aan een advertentieserver, omvat de reactie VAST/VMAP gewoonlijk veelvoudige ad creatieve ( `MediaFile` elementen), elk waarvan een URL aan een verschillende container-codec versie verstrekt. In sommige gevallen bieden ad-hocgeneesmiddelen in de VAST/VMAP-respons elk een andere bitsnelheid voor de advertentie. Als u uw eigen prioriteit en transformatieregels voor deze en creatieve toevoegingen wilt specificeren, kunt u dit in het [!DNL AdobeTVSDKConfig.json] configuratiedossier doen.

>[!IMPORTANT]
>
>* Wijzig de naam van het configuratiebestand voor TVSDK niet. De naam moet [!DNL AdobeTVSDKConfig.json] blijven.
>* Dit bestand moet worden gehost op het CDN (Content Delivery Network).

>



U kunt twee typen regels opgeven in [!DNL AdobeTVSDKConfig.json]: *Prioriteitsregels* en *Normaliseren* regels.
