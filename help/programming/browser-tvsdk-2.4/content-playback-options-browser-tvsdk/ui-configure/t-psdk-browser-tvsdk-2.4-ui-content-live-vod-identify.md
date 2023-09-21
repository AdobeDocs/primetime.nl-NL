---
description: Mogelijk moet u weten of de media-inhoud live of VOD is.
title: Identificeer of de inhoud live of VOD is
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---

# Identificeer of de inhoud live of VOD is{#identify-whether-the-content-is-live-or-vod}

Mogelijk moet u weten of de media-inhoud live of VOD is.

1. Wacht tot Browser TVSDK een `AdobePSDK.PSDKEventType.STATUS_CHANGED` gebeurtenis met een `event.status` van `AdobePSDK.MediaPlayerStatus.PREPARED`.

   Deze stap zorgt ervoor dat de mediabron correct is geladen.

   >[!IMPORTANT]
   >
   >Als de TVSDK van de browser zich niet in ten minste de `PREPARED` status, wordt bij een poging de volgende methoden aan te roepen een `IllegalStateException`.

1. Lezen `live` van de `MediaPlayerItem` interface:

   ```js
   player.currentItem.live
   ```
