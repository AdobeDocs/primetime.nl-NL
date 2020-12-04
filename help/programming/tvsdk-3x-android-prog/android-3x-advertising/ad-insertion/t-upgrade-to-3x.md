---
description: 'De interface com.adobe.mediacore.timeline.TimelineMarker bevat nu een nieuwe methode '
seo-description: 'De interface com.adobe.mediacore.timeline.TimelineMarker bevat nu een nieuwe methode '
seo-title: 'Opwaarderen vanaf 2.5.x Lazy Ad Resolving to 3.0.0 Lazy Ad Resolving (API/Workflow changes) '
title: 'Opwaarderen vanaf 2.5.x Lazy Ad Resolving to 3.0.0 Lazy Ad Resolving (API/Workflow changes) '
uuid: 5870ceb4-93a8-4c8b-b716-673396122644
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Een upgrade uitvoeren van 2.5.x Lazy Ad Resolving naar 3.x Lazy Ad Resolving (API/workflowwijzigingen):{#upgrading-from-x-lazy-ad-resolving-to-lazy-ad-resolving-api-workflow-changes}

De interface com.adobe.mediacore.timeline.TimelineMarker bevat nu een nieuwe methode:

**Placement.Type getPlacementType()**

Deze methode retourneert een plaatsingstype van Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL of Placement.Type.POST_ROLL. Als een ad-einde niet is opgelost, retourneert de methode `getDuration()`op de interface TimelineMarker 0.

>[!NOTE]
>
>Deze interface wordt niet altijd gecast naar het type com.mediacore.timeline.advertence.AdBreakTimelineItem als dit nog niet is opgelost. Het zal kunnen worden gecast als de `getDuration()` methode van TimelineMarker groter is dan 0.

**Wijzigingen in gebeurtenis:**

`kEventAdResolutionComplete` wordt nu afgeschreven en wordt nu geactiveerd onmiddellijk nadat de speler de status PREPARED heeft gekregen. Toepassingen die eerder alleen naar deze gebeurtenis hebben geluisterd om de scrubbalk te tekenen, moeten dit wijzigen om alleen naar `kEventTimelineUpdated` te luisteren. Nadat afzonderlijke ad-einden zijn opgelost, wordt een nieuwe `kEventTimelineUpdated`-gebeurtenis verzonden.
