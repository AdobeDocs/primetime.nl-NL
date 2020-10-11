---
cloud: experience-cloud
product: adobe primetime
audience: end-user
user-guide-title: Help bij primetime Dynamic Ad Insertion
user-guide-description: Explains how to monetize content by inserting user-targeted dynamic ads on the server and engage audience with personalized ads.
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Help bij Dynamic Ad Insertion {#ad-insertion}

+ [Dynamisch Ad Insertion-overzicht](home.md)
+ Aan de slag met Primetime Ad Insertion{#get-started}
   + [Overzicht](get-started-ptai.md)
   + [Voorbereiden op het gebruik van Primetime Ad Insertion](setup-ptai.md)
   + [Uw advertentieserver integreren](integrate-ad-server.md)
   + [Uw CDN integreren](integrate-cdn.md)
   + [Toevoegen en invoegen in live/lineaire streams gebruiken](ad-insertion-live-linear-stream.md)
   + [Toevoegen en invoegen voor VOD gebruiken](ad-insertion-vod.md)
   + [Opzetten en bijhouden](set-up-ad-tracking.md)
+ [Opmerkingen bij de release Dynamic Ad Insertion](https://docs.adobe.com/content/help/en/primetime/release-notes/ptai/ptai-19x-release-notes.html)
+ [Foutopsporingsprogramma voor server Manifest](manifest-server-debugging-tool.md)

<!-- + [Server Side Ad Insertion debugging dashboard](ssai-debugging-dashboard.md)-->
+ Manifest Server-API voor Ad Insertion {#manifest-server}
   + [Overzicht van Manifest Server-interacties](msapi-topics/ms-overview.md)
   + Aan de slag met Manifest Server {#get-started}
      + [Een opdracht naar de manifest-server verzenden](msapi-topics/ms-getting-started/ms-sending-cmd.md)
      + [Query-parameters van de server manipuleren](msapi-topics/ms-getting-started/ms-api-query-params.md)
   + Aanvragen voor invoeging toevoegen {#ad-insert}
      + [Verzoek om inlassing](msapi-topics/ms-insert-ads/ms-ad-insert.md)
      + [Optionele queryparameters per client en situatie](msapi-topics/ms-insert-ads/ms-api-query-param-situation.md)
      + [HLS-speler helpen overschakelen naar failover-/back-upstreams](msapi-topics/ms-insert-ads/hls-switching-to-failover.md)
      + [Streams met meerdere bitsnelheden](msapi-topics/ms-insert-ads/ms-api-mbr-streams.md)
      + [Gedeeltelijke invoeging van advertentie-einde](msapi-topics/ms-insert-ads/partial-ad-break-insetion.md)
      + [Meerdere CDN-ondersteuning voor CRS en levering](msapi-topics/ms-insert-ads/ms-api-multi-cdns-for-crs.md)
   + VOD-tijdlijnen vervangen {#replace-vod}
      + [Wijzigingen in VOD](msapi-topics/ms-changes-vod-timeline/ms-replace-vod-timeline.md)
      + [Tijdlijnindeling VOD](msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)
      + [Een VOD-tijdlijn vervangen](msapi-topics/ms-changes-vod-timeline/t-ms-replace-vod-timeline.md)
   + Doeltreffendheid bijhouden {#ad}
      + [Advertentie bijhouden](msapi-topics/ms-at-effectiveness/ms-at-overview.md)
      + [Enable client-side ad tracking](msapi-topics/ms-at-effectiveness/ms-enable-client-side-ad-tracking.md)
      + [Overzicht van niet-TVSDK client-side tracking](msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md)
      + [API voor spelers om te communiceren met de manifestserver](msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)
      + [EXT-X-MARKERINGSrichtlijn](msapi-topics/ms-at-effectiveness/ms-api-playlists.md)
   + [Cookies](msapi-topics/ms-cookies.md)
   + [Ondersteuning voor WebVTT-bijschriften](msapi-topics/ms-webvtt-captions.md)
   + Lijst met bestandsindelingen {#list}
      + [Bestandsindelingen](msapi-topics/ms-list-file-formats/ms-api-file-formats.md)
      + [JSON-indeling voor URL voor het aanvragen van afspeellijst met variantmanifest](msapi-topics/ms-list-file-formats/ms-json-m3u8.md)
      + [JSON-indelingen voor het bijhouden van URL&#39;s](msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md)
      + [VMAP-indeling voor het bijhouden van URL&#39;s](msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md)
   + [Vereisten voor videospeler](msapi-topics/ms-player-req.md)
+ Primetime Creative Repacking Service {#crs}
   + [Overzicht van CRS](creative-repackaging-service/crs-overview.md)
   + [Belangrijkste toepassingen van CRS](creative-repackaging-service/jit-async-hls-conv.md)
   + [Ondersteuning voor Multi CDN](creative-repackaging-service/multi-cdn-supportt.md)
   + [Gedetailleerde workflows voor JIT-herverpakken](creative-repackaging-service/jit-repackage.md)
   + [CRS gebruiken om ID3-tags met getimede metagegevens te injecteren](creative-repackaging-service/inject-id3.md)
   + [API opnieuw verpakken](creative-repackaging-service/api-repackage.md)
