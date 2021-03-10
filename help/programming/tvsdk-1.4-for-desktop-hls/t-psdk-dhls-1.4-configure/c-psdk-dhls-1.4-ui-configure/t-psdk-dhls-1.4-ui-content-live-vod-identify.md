---
description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
title: Identificeer of de inhoud live of VOD is
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# Identificeer of de inhoud live of VOD{#identify-whether-the-content-is-live-or-vod} is

In sommige gevallen moet u weten of de media-inhoud live of VOD is.

1. Zorg ervoor dat de speler ten minste de status INITIALIZED heeft.
1. Bepaal of de `MediaPlayerItem`-inhoud live (true) of VOD (false) is.

   ```
   function get isLive():Boolean;
   ```

