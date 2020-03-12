---
description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
seo-description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
seo-title: Identificeer of de inhoud live of VOD is
title: Identificeer of de inhoud live of VOD is
uuid: d49315ee-8cec-4b79-adbd-a49c2a527424
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Identificeer of de inhoud live of VOD is {#identify-whether-the-content-is-live-or-vod}

Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).

1. Zorg ervoor dat de speler zich ten minste in de `PREPARED` status bevindt.
1. Bepaal of de `MediaPlayerItem` inhoud live ( `true`) of VOD ( `false`) is.

   ```java
   boolean isLive();
   ```
