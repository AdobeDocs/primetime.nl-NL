---
description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
title: Identificeer of de inhoud live of VOD is
exl-id: a75332d9-a23a-423c-8d1f-81b40ca73b21
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---

# Identificeer of de inhoud live of VOD is {#identify-whether-the-content-is-live-or-vod}

Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).

1. Zorg ervoor dat de speler zich op zijn minst in de `PREPARED` status.
1. Bepalen of de `MediaPlayerItem` content is live ( `true`) of VOD ( `false`).

   ```java
   boolean isLive();
   ```
