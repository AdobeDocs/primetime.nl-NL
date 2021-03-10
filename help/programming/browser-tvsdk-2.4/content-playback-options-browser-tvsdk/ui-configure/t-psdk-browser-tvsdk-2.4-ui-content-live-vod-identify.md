---
description: Mogelijk moet u weten of de media-inhoud live of VOD is.
title: Identificeer of de inhoud live of VOD is
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '85'
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

