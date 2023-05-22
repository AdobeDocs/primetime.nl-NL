---
description: De interface com.adobe.mediacore.timeline.TimelineMarker bevat nu een nieuwe methode
title: Opwaarderen vanaf 2.5.x Lazy Ad Resolving to 3.0.0 Lazy Ad Resolving (API/Workflow changes)
exl-id: 403ccb25-99a9-4545-9d17-3b71583bc6d8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Upgrade van 2.5.x Lazy Ad Resolving naar 3.x Lazy Ad Resolving (API/Workflow changes):{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

De interface com.adobe.mediacore.timeline.TimelineMarker bevat nu een nieuwe methode:

**Placement.Type getPlacementType()**

Deze methode retourneert een plaatsingstype van Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL of Placement.Type.POST_ROLL. Als een ad-einde niet is opgelost, wordt het `getDuration()`methode op de interface TimelineMarker retourneert 0.

>[!NOTE]
>
>Deze interface wordt niet altijd gecast naar het type com.mediacore.timeline.advertence.AdBreakTimelineItem als dit nog niet is opgelost. Als de `getDuration()` de methode TimelineMarker is groter dan 0.

**Wijzigingen in gebeurtenis:**

`kEventAdResolutionComplete` wordt nu afgeschreven en wordt nu geactiveerd onmiddellijk nadat de speler de status PREPARED heeft gekregen. Toepassingen die eerder alleen naar deze gebeurtenis hebben geluisterd om de scrubbalk te tekenen, moeten dit wijzigen om te luisteren naar `kEventTimelineUpdated` alleen. Nadat afzonderlijke advertentieafbrekingen zijn opgelost, wordt een nieuwe `kEventTimelineUpdated` -gebeurtenis wordt verzonden.
