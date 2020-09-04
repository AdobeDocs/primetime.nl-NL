---
description: Het downloaden van video en audio parallel, eerder dan in een reeks, vermindert startvertragingen.
seo-description: Het downloaden van video en audio parallel, eerder dan in een reeks, vermindert startvertragingen.
seo-title: Parallelle downloads
title: Parallelle downloads
uuid: fa3edb50-7c24-433c-bc50-72d6cf73d834
translation-type: tm+mt
source-git-commit: 51b3713e04fcb4adeaa7a8d1b700372b1dba7cf6
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# Parallelle downloads {#parallel-downloads}

Het downloaden van video en audio parallel, eerder dan in een reeks, vermindert startvertragingen.

Parallelle downloads maken het mogelijk video-op-verzoek-bestanden (VOD) af te spelen, optimaliseren het beschikbare bandbreedtegebruik van een server, verminderen de kans om in situaties waarin de buffer onderloopt te raken en minimaliseren de vertraging tussen downloaden en playback.

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

Zonder parallelle downloads, geeft TVSDK een verzoek voor het videosegment uit, en nadat het videosegment wordt geladen, vraagt het één of twee audiosegmenten. Bij parallelle downloads worden de audio- en videosegmenten tegelijkertijd gedownload, niet opeenvolgend. Bovendien bereiken de gegevens het scherm sneller, omdat er twee verbindingen en twee HTTP-aanvragen tegelijk zijn.

>[!NOTE]
>
>Deze functie is alleen van toepassing op inhoud waarbij de audio en video in verschillende bestanden worden gecodeerd (ongedempte inhoud) en is niet van toepassing op MP4-inhoud, die altijd wordt gedempt. HLS-inhoud is vaak niet-gedempt, met name bij alternatieve audio.

<!-- 

See comment above (DASH use case removed).
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
-->

De verbinding van HTTP zou vertragingen in de volgende stadia kunnen ervaren:

* Bij het tot stand brengen van een TCP/IP-verbinding met de server

   Hoewel de client en de server zijn overeengekomen te communiceren, is er nog geen HTTP-communicatie opgetreden. Dit type vertraging is afhankelijk van de infrastructuur tussen de client en de server. Dit proces vereist het vinden van een weg door Internet tussen de cliënt en de server en het ervoor zorgen alle apparaten, zoals routers en firewalls, op de route met de gegevensoverdracht akkoord gaat.
* Wanneer het verzenden van een HTTP- verzoek om een segment of manifest over de verbinding TCP/IP.

   De server ontvangt het verzoek, verwerkt het, en begint de gegevens terug naar de cliënt te verzenden. De mate van vertraging is afhankelijk van de lading en de ingewikkeldheid van de software op de server en enigszins van de snelheid van de uploadverbinding wanneer de cliënt het verzoek verzendt.

