---
description: Vanaf Flash 15 en hoger geldt dat wanneer geen hardware-rendering met StageVideo beschikbaar is, StageVideo naadloos terugvalt naar een software StageVideo-object.
title: Flash 15-ondersteuning voor StageVideo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
* Uw toepassingen moeten voor Flash 15 opnieuw worden samengesteld.
* Toepassingen die u opnieuw compileert voor Flash 15, blijven werken met Flash 14 en eerder, zolang deze toepassingen geen nieuwe APIs gebruiken die in Flash Player 15 werden geïntroduceerd.

  Als uw Flash 14 toepassing een nieuwe Flash 15 API moet gebruiken, moet u dynamisch API met een gietvorm aan het type van Objecten roepen, zodat de toepassing niet in Flash Player 14 bij runtime ontbreekt.

## HTML-bedekkingen {#html-overlays}

In Flash 15 en hoger kunt u een naadloze weergave van HTML-overlays behouden wanneer de hardware StageVideo niet beschikbaar is en terugvalt naar de software StageVideo. Als u deze functie wilt inschakelen, stelt u `wmode=opaque`.

Sommige oudere browsers ondersteunen hardwareversnelling niet. Zie voor meer informatie over deze vereisten [Minimumvereisten voor StageVideo](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Wanneer u instelt `wmode=opaque`, wordt de video gerenderd met software StageVideo, wat de prestaties kan beïnvloeden. Normaal gesproken instellen `wmode=direct` Hiermee wordt video direct gerenderd naar GPU, wat resulteert in veel betere prestaties. Deze optie heeft echter ook voorrang op HTML-overlays.
