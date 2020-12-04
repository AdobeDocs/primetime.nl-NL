---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
seo-title: Metagegevens voor invoeging toevoegen
title: Metagegevens voor invoeging toevoegen
uuid: 3eb024c3-4bb5-4bee-943e-fe0c60379e60
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# Metagegevens voor invoeging toevoegen {#ad-insertion-metadata}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

TVSDK bevat de Primetime- en beslissingsbibliotheek. Uw toepassing moet de volgende vereiste `AuditudeSettings`-informatie opgeven om uw inhoud ook reclame van de Primetime- en beslissingsserver te kunnen opnemen:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de media-id toe bij het verzenden van video-inhoud en advertentiegegevens naar de Adobe Primetime en de beslissingsserver. Deze id wordt gebruikt door Primetime en door beslissingen om gerelateerde advertentiegegevens voor de video op te halen van de server.

* Uw `zoneID`, die door Adobe wordt toegewezen, identificeert uw bedrijf of website.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.

## Metagegevens instellen en invoegen {#set-up-ad-insertion-metadata}

Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.

>[!TIP]
>
>Adobe Primetime en de beslissing stond voorheen bekend als Auditude.

Metagegevens voor reclame bevinden zich in de eigenschap `MediaResource.metadata`. Wanneer u begint met het afspelen van een nieuwe video, is uw toepassing verantwoordelijk voor het instellen van de juiste metagegevens voor advertenties.

1. Stel de instantie `AuditudeSettings` samen.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Stel de Adobe Primetime- en beslissingsmedia-id, zoneID, domain en de optionele parameters voor toewijzen in.

   ```
   auditudeSettings.zoneId = "yourZoneID"; 
   auditudeSettings.mediaId = "media_identifier"; 
   auditudeSettings.domain = "yourAuditudeDomain"; 
   var targetingInfo:Metadata = new Metadata(); 
   targetingInfo.setValue("yourParamName", "yourParamValue"); 
   auditudeSettings.targetingInfo = targetingInfo;
   ```

   >[!TIP]
   >
   >De media-id wordt door TVSDK gebruikt als een tekenreeks, die wordt omgezet in een md5-waarde en wordt gebruikt voor de waarde `u` in het URL-verzoek voor primetime en besluitvorming. Bijvoorbeeld:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Maak een `MediaResource`-instantie met de URL van de mediastream en de eerder gemaakte advertentiemetagegevens.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Laad het object `MediaResource` via de methode `MediaPlayer.replaceCurrentResource`.

   Met `MediaPlayer` wordt het mediabream geladen en verwerkt.

1. (Optioneel) Vraag de instantie `MediaPlayerItem` om te zien of de stream live is, ongeacht of deze alternatieve audiotracks heeft of of de stream is beveiligd.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bel `MediaPlayer.prepareToPlay` om de advertentieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, gaat `MediaPlayer` over naar de status PREPARED.
1. Roep `MediaPlayer.play` aan om het afspelen te starten.

TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.