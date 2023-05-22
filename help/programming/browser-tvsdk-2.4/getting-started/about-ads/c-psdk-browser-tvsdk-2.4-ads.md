---
description: Wanneer inhoud wordt afgespeeld, kan Browser-TVSDK tijdens het maken van het MediaResource-object advertenties weergeven en informatie over advertenties doorgeven.
title: Adds
exl-id: a44ad0fa-841f-474b-89f4-39666190231f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Overzicht {#ads-overview}

Wanneer inhoud wordt afgespeeld, kan Browser-TVSDK tijdens het maken van het MediaResource-object advertenties weergeven en informatie over advertenties doorgeven.

U kunt optioneel de `prepareToPlay` functie nadat u `AdobePSDK.MediaPlayerStatus.INITIALIZED`.

```js
function onStatusChange (event) { 
   switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
        player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
        break; 
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
        player.play(); 
        break; 
   } 
} 
 
var auditudeSettings     = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.domain  = "sample_auditude_domain"; 
auditudeSettings.mediaId = "sample_media_id"; 
auditudeSettings.zoneId  = "sample_zone_id"; 
 
// event handler 
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
 
var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
```

Browser TVSDK verstrekt ook de volgende ad-specifieke gebeurtenissen die u in uw gebeurtenismanagers kunt gebruiken om inhoud te verhinderen snel door:sturen wanneer de advertenties spelen:

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`
* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

Om dit werkend in het Kader te zien UI, specificeer advertentie montages in configuratie als volgt:

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource: { 
 
            resourceUrl:'Specify Resource Url', 
 
            auditudeSettings: { 
                validMimeTypes: ["application/x-mpeURL"], 
                domain: "Sample_auditude_domain", 
                mediaId:"sample_media_id", 
                zoneID:"sample_zone_id", 
                creativeRepackagingEnabled:true 
            } 
        } 
    } 
}; 
```

Voor meer informatie over de vereiste `AuditudeSettings`, zie [Metagegevens voor invoeging toevoegen](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md).
