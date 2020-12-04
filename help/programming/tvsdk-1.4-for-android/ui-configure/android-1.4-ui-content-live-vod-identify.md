---
description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
seo-description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
seo-title: Identificeer of de inhoud live of VOD is
title: Identificeer of de inhoud live of VOD is
uuid: cd71b8d3-259a-48f8-a6ad-02b57da146a7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# Identificeer of de inhoud live of VOD{#identify-whether-the-content-is-live-or-vod} is

In sommige gevallen moet u weten of de media-inhoud live of VOD is.

1. Zorg ervoor dat de speler zich ten minste in de staat PREPARED bevindt.
1. Bepaal of de `MediaPlayerItem`-inhoud live (true) of VOD (false) is.

   ```java
   boolean isLive();
   ```

