---
description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
title: Identificeer of de inhoud live of VOD is
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Identificeer of de inhoud live of VOD is{#identify-whether-the-content-is-live-or-vod}

In sommige gevallen moet u weten of de media-inhoud live of VOD is.

1. Zorg ervoor dat de speler ten minste de status INITIALIZED heeft.
1. Bepalen of de `MediaPlayerItem` content is live (true) of VOD (false).

   ```
   function get isLive():Boolean;
   ```
