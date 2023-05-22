---
description: In sommige gevallen moet u weten of de media-inhoud live of VOD is.
title: Identificeer of de inhoud live of VOD is
exl-id: b93cc61b-aa72-4edd-a070-93c111dec339
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# Identificeer of de inhoud live of VOD is{#identify-whether-the-content-is-live-or-vod}

In sommige gevallen moet u weten of de media-inhoud live of VOD is.

1. Zorg ervoor dat de speler zich ten minste in de staat PREPARED bevindt.
1. Bepalen of de `MediaPlayerItem` content is live (true) of VOD (false).

   ```java
   boolean isLive();
   ```
