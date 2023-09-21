---
description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
title: Identificeer of de inhoud live of VOD is
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
