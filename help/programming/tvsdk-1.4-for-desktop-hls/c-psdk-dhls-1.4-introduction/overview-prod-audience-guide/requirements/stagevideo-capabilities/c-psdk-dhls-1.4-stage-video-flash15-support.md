---
description: Wanneer geen hardwarerendering met StageVideo beschikbaar is, valt StageVideo vanaf Flash 15 en hoger naadloos terug naar een software StageVideo-object.
seo-description: Wanneer geen hardwarerendering met StageVideo beschikbaar is, valt StageVideo vanaf Flash 15 en hoger naadloos terug naar een software StageVideo-object.
seo-title: Flash 15-ondersteuning voor StageVideo
title: Flash 15-ondersteuning voor StageVideo
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Flash 15-ondersteuning voor StageVideo{#flash-support-for-stagevideo}

Wanneer geen hardwarerendering met StageVideo beschikbaar is, valt StageVideo vanaf Flash 15 en hoger naadloos terug naar een software StageVideo-object.

Bekijk de volgende informatie over de Flash 15 StageVideo-fallback naar software:

* Er zijn geen wijzigingen in de code vereist in de toepassing.
* U hoeft de TVSDK niet te wijzigen.

   U hebt geen TVSDK-update nodig om StageVideo-fallback naar software te gebruiken.
* Uw toepassingen moeten opnieuw worden gecompileerd voor Flash 15.
* Toepassingen die u opnieuw compileert voor Flash 15, blijven werken met Flash 14 en eerder, zolang deze toepassingen geen nieuwe API&#39;s gebruiken die zijn geïntroduceerd in Flash Player 15.

   Als uw Flash 14-toepassing een nieuwe Flash 15-API moet gebruiken, moet u de API dynamisch aanroepen met een cast naar het type Object, zodat de toepassing tijdens runtime niet in Flash Player 14 mislukt.

## HTML-overlays {#html-overlays}

In Flash 15 en hoger kunt u een naadloze weergave van HTML-overlays behouden wanneer hardware StageVideo niet meer beschikbaar is en terugvalt naar software StageVideo. Stel deze functie in om deze functie in te schakelen `wmode=opaque`.

Sommige oudere browsers ondersteunen hardwareversnelling niet. Zie Minimumvereisten voor [StageVideo voor meer informatie over deze vereisten](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). Wanneer u deze instelt, wordt de video gerenderd met software StageVideo, wat van invloed kan zijn op de prestaties. `wmode=opaque` Als u de video instelt, wordt deze meestal `wmode=direct` rechtstreeks gerenderd naar GPU. Dit levert veel betere prestaties op. Deze optie negeert echter ook HTML-overlays.
