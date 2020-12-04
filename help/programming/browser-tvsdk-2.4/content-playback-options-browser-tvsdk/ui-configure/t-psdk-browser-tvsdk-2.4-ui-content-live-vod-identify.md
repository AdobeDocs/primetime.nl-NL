---
description: Mogelijk moet u weten of de media-inhoud live of VOD is.
seo-description: Mogelijk moet u weten of de media-inhoud live of VOD is.
seo-title: Identificeer of de inhoud live of VOD is
title: Identificeer of de inhoud live of VOD is
uuid: 5455801e-b5eb-4829-bde6-ef4440cd69c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Identificeer of de inhoud live of VOD{#identify-whether-the-content-is-live-or-vod} is

Mogelijk moet u weten of de media-inhoud live of VOD is.

1. Wacht op Browser TVSDK om een `AdobePSDK.PSDKEventType.STATUS_CHANGED` gebeurtenis met `event.status` van `AdobePSDK.MediaPlayerStatus.PREPARED` teweeg te brengen.

   Deze stap zorgt ervoor dat de mediabron correct is geladen.

   >[!IMPORTANT]
   >
   >Als Browser TVSDK niet in minstens de `PREPARED` staat is, werpt het proberen om de volgende methodes te roepen `IllegalStateException`.

1. Lees `live` van de `MediaPlayerItem` interface:

   ```js
   player.currentItem.live
   ```

