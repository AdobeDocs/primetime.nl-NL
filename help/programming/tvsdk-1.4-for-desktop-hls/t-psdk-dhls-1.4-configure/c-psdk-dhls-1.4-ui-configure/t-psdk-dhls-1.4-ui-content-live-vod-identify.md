---
description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
seo-description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
seo-title: Identificeer of de inhoud live of VOD is
title: Identificeer of de inhoud live of VOD is
uuid: 4d514c46-a1d0-4721-a423-92108126e37e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Identificeer of de inhoud live of VOD is{#identify-whether-the-content-is-live-or-vod}

In sommige gevallen moet u weten of de media-inhoud live of VOD is.

1. Zorg ervoor dat de speler ten minste de status INITIALIZED heeft.
1. Bepaal of de `MediaPlayerItem` inhoud live (true) of VOD (false) is.

   ```
   function get isLive():Boolean;
   ```

