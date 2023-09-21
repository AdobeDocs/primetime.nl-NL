---
title: Essentiële bewerkingen bij het afspelen van video
description: De PlaybackManager biedt essentiële bewerkingen van HLS-streaming
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
