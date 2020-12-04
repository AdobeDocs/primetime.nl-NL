---
description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
seo-description: Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).
seo-title: Identificeer of de inhoud live of VOD is
title: Identificeer of de inhoud live of VOD is
uuid: e6a66104-97fb-438a-8356-e21f94058c85
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Identificeer of de inhoud live of VOD {#identify-whether-the-content-is-live-or-vod} is

Mogelijk moet u weten of de media-inhoud live is of video op verzoek (VOD).

1. Zorg ervoor dat de speler zich in minstens de status `PREPARED` bevindt.
1. Bepaal of de `MediaPlayerItem`-inhoud live ( `true`) of VOD ( `false`) is.

   ```java
   boolean isLive();
   ```
