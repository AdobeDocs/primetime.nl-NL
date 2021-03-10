---
title: Essentiële bewerkingen bij het afspelen van video
description: De PlaybackManager biedt essentiële bewerkingen van HLS-streaming
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Essentiële bewerkingen bij het afspelen van video {#essential-operations-of-video-playback}

De PlaybackManager biedt essentiële bewerkingen van HLS-streaming:

* Roept [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html) aan, die geschikt aan videogebeurtenissen kan antwoorden.
* Biedt een afspeelbewerking, zoals afspelen, pauzeren en zoeken.
* Retourneert de informatie over de speler, zoals de status van de speler, het afspeelbereik en de live videostream.
* Hiermee wordt bepaald of ABR is ingeschakeld en worden de parameters voor ABR en bufferbeheer ingesteld, afhankelijk van de verschafte configuratiegegevens.
* Hiermee wordt bepaald of bufferbesturing is ingeschakeld en worden de parameters voor bufferbesturing ingesteld, afhankelijk van de opgegeven configuratiegegevens.