---
title: Essentiële bewerkingen bij het afspelen van video
description: De PlaybackManager biedt essentiële bewerkingen van HLS-streaming
exl-id: b4d1b41a-7a16-47f5-be88-6b52f0451813
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Essentiële bewerkingen bij het afspelen van video {#essential-operations-of-video-playback}

De PlaybackManager biedt essentiële bewerkingen van HLS-streaming:

* Roept de [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html), die op de juiste manier op videogebeurtenissen kan reageren.
* Biedt een afspeelbewerking, zoals afspelen, pauzeren en zoeken.
* Retourneert de informatie over de speler, zoals de status van de speler, het afspeelbereik en de live videostream.
* Hiermee wordt bepaald of ABR is ingeschakeld en worden de parameters voor ABR en bufferbeheer ingesteld, afhankelijk van de verschafte configuratiegegevens.
* Hiermee wordt bepaald of bufferbesturing is ingeschakeld en worden de parameters voor bufferbesturing ingesteld, afhankelijk van de opgegeven configuratiegegevens.
