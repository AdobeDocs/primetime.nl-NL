---
description: Vanaf Flash 15 en hoger geldt dat wanneer geen hardware-rendering met StageVideo beschikbaar is, StageVideo naadloos terugvalt naar een software StageVideo-object.
title: Flash 15-ondersteuning voor StageVideo
exl-id: 23ef0806-3aa5-4c48-a4f7-4ad9b72bdcc9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Flash 15-ondersteuning voor StageVideo{#flash-support-for-stagevideo}

Vanaf Flash 15 en hoger geldt dat wanneer geen hardware-rendering met StageVideo beschikbaar is, StageVideo naadloos terugvalt naar een software StageVideo-object.

Bekijk de volgende informatie over de Flash 15 StageVideo-fallback naar software:

* Er zijn geen wijzigingen in de code vereist in de toepassing.
* U hoeft de TVSDK niet te wijzigen.

   U hebt geen TVSDK-update nodig om StageVideo-fallback naar software te gebruiken.
* Uw toepassingen moeten opnieuw worden gecompileerd voor Flash 15.
* Toepassingen die u opnieuw compileert voor Flash 15, blijven werken met Flash 14 en eerder, zolang deze toepassingen geen nieuwe API&#39;s gebruiken die zijn geïntroduceerd in Flash Player 15.

   Als uw Flash 14-toepassing een nieuwe Flash 15-API moet gebruiken, moet u de API dynamisch aanroepen met een cast naar het objecttype, zodat de toepassing niet in Flash Player 14 mislukt bij uitvoering.

## HTML-bedekkingen {#html-overlays}

In Flash 15 en hoger kunt u een naadloze weergave van HTML-overlays behouden wanneer de hardware StageVideo niet beschikbaar is en terugvalt naar de software StageVideo. Als u deze functie wilt inschakelen, stelt u `wmode=opaque`.

Sommige oudere browsers ondersteunen hardwareversnelling niet. Zie voor meer informatie over deze vereisten [Minimumvereisten voor StageVideo](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Wanneer u `wmode=opaque`, wordt de video gerenderd met software StageVideo, wat de prestaties kan beïnvloeden. Normaal gesproken instellen `wmode=direct` Hiermee wordt video direct gerenderd naar GPU, wat resulteert in veel betere prestaties. Deze optie heeft echter ook voorrang op HTML-overlays.
