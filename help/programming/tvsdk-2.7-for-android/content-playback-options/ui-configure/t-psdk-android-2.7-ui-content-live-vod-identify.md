---
description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
title: Identificeer of de inhoud live of VOD is
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# Identificeer of de inhoud live of VOD {#identify-whether-the-content-is-live-or-vod} is

Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).

1. Zorg ervoor dat de speler zich in minstens de status `PREPARED` bevindt.
1. Bepaal of de `MediaPlayerItem`-inhoud live ( `true`) of VOD ( `false`) is.

   ```java
   boolean isLive();
   ```
