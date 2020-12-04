---
description: Vanaf Flash 15 en hoger geldt dat wanneer geen hardware-rendering met StageVideo beschikbaar is, StageVideo naadloos terugvalt naar een software StageVideo-object.
seo-description: Vanaf Flash 15 en hoger geldt dat wanneer geen hardware-rendering met StageVideo beschikbaar is, StageVideo naadloos terugvalt naar een software StageVideo-object.
seo-title: Flash 15-ondersteuning voor StageVideo
title: Flash 15-ondersteuning voor StageVideo
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '271'
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

## HTML-overlays {#html-overlays}

In Flash 15 en hoger kunt u een naadloze weergave van HTML-overlays behouden wanneer de hardware StageVideo niet beschikbaar is en terugvalt naar de software StageVideo. Stel `wmode=opaque` in om deze functie in te schakelen.

Sommige oudere browsers ondersteunen hardwareversnelling niet. Zie [Minimumeisen voor StageVideo](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md) voor meer informatie over deze vereisten. Wanneer u `wmode=opaque` instelt, wordt de video gerenderd met software StageVideo, wat de prestaties kan beïnvloeden. Als u `wmode=direct` instelt, wordt video doorgaans direct gerenderd naar GPU, wat resulteert in veel betere prestaties. Deze optie negeert echter ook HTML-overlays.
