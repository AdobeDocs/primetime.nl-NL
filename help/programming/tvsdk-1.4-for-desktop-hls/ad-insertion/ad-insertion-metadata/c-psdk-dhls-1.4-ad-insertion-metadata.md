---
description: Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.
title: Metagegevens voor invoeging toevoegen
exl-id: 83c0fd25-dbc3-4529-b81a-16ff78012c80
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Metagegevens voor invoeging toevoegen {#ad-insertion-metadata}

Als u de advertentieoplosser wilt laten werken, hebben providers, zoals Adobe Primetime en besluitvorming, configuratiewaarden nodig om de verbinding met de provider mogelijk te maken.

TVSDK bevat de Primetime- en beslissingsbibliotheek. Uw toepassing moet het volgende opgeven om uw inhoud ook reclame van de Primetime- en beslissingsserver te laten opnemen `AuditudeSettings` informatie:

* `mediaID`Dit is een unieke id voor de video die moet worden afgespeeld.

   De uitgever wijst de media-id toe bij het verzenden van video-inhoud en advertentiegegevens naar de Adobe Primetime en de beslissingsserver. Deze id wordt gebruikt door Primetime en door beslissingen om gerelateerde advertentiegegevens voor de video op te halen van de server.

* Uw `zoneID`, die wordt toegewezen door Adobe, uw bedrijf of website identificeert.
* Het domein van de toegewezen advertentieserver.
* Andere doelparameters.

   U kunt deze parameters opnemen, afhankelijk van uw behoeften en de behoeften van de advertentieprovider.

## Metagegevens instellen en invoegen {#set-up-ad-insertion-metadata}

Met de hulpklasse AuditudeSettings, die de klasse MetadataNode uitbreidt, kunt u Adobe Primetime- en beslissingsmetagegevens instellen.

>[!TIP]
>
>Adobe Primetime en de beslissing stond voorheen bekend als Auditude.

Metagegevens over reclame bevinden zich in de `MediaResource.metadata` eigenschap. Wanneer u begint met het afspelen van een nieuwe video, is uw toepassing verantwoordelijk voor het instellen van de juiste metagegevens voor advertenties.

1. De `AuditudeSettings` -instantie.

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
   >De media-id wordt door TVSDK gebruikt als een tekenreeks, die wordt omgezet in een md5-waarde en wordt gebruikt voor de `u` waarde in het Primetime- en beslissings-URL-verzoek. Bijvoorbeeld:
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. Een `MediaResource` door de URL van de mediastream en de eerder gemaakte advertentiemetagegevens te gebruiken.

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. Laad de `MediaResource` door het `MediaPlayer.replaceCurrentResource` methode.

   De `MediaPlayer` start met het laden en verwerken van het mediastroommanifest.

1. (Optioneel) Zoek naar de `MediaPlayerItem` -instantie om te zien of de stream live is, ongeacht of er alternatieve audiotracks zijn of of de stream is beveiligd.

   Deze informatie kan u helpen UI voor het playback voorbereiden. Als u bijvoorbeeld weet dat er twee audiotracks zijn, kunt u een UI-besturingselement opnemen dat schakelt tussen deze tracks.

1. Bellen `MediaPlayer.prepareToPlay` om de publicatieworkflow te starten.

   Nadat de advertenties zijn opgelost en op de tijdlijn zijn geplaatst, wordt het `MediaPlayer` overgangen naar de status PREPARED.
1. Bellen `MediaPlayer.play` om het afspelen te starten.

TVSDK bevat nu advertenties wanneer uw media wordt afgespeeld.
