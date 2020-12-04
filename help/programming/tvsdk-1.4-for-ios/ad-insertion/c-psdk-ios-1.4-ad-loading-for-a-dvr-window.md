---
description: U kunt beslissen of alleen de advertenties worden opgelost die na het huidige actieve punt van de gebruiker optreden of dat ook advertenties worden opgelost die vóór het huidige actieve punt plaatsvinden.
seo-description: U kunt beslissen of alleen de advertenties worden opgelost die na het huidige actieve punt van de gebruiker optreden of dat ook advertenties worden opgelost die vóór het huidige actieve punt plaatsvinden.
seo-title: Advertentie laden voor een DVR-venster
title: Advertentie laden voor een DVR-venster
uuid: 67bc3924-3d17-4d1a-b9a7-be8d0488a970
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Advertentie laden voor een DVR-venster {#load-ad-for-a-dvr-window}

U kunt beslissen of alleen de advertenties worden opgelost die na het huidige actieve punt van de gebruiker optreden of dat ook advertenties worden opgelost die vóór het huidige actieve punt plaatsvinden.

Wanneer een gebruiker inhoud begint te bekijken aan het begin van een DVR-stream, lost TVSDK alle advertenties voor de stream op dat moment op. Wanneer de gebruiker echter inhoud begint weer te geven op een punt na het begin van de stream, kunt u beslissen of alleen de advertenties worden opgelost die na het huidige actieve punt van de gebruiker optreden of dat ook advertenties worden opgelost die vóór het huidige actieve punt zijn opgetreden.

>[!TIP]
>
>Het omzetten van advertenties na het huidige actieve punt gaat sneller, maar als de gebruiker achterwaarts zoekt, voorkomt u met deze optie dat de speler advertenties afspeelt die eerder zijn weergegeven.

## Controle en lading voor een venster DVR {#section_2D93E2E947644D66B6F6ED1DD6742C25}

U kunt als volgt een DVR-venster besturen en laden:

Als u alle advertenties voor de gehele stream wilt laden, stelt u de eigenschap `PTAdMetadata.enableDVRAds` in op `YES`.

>[!NOTE]
>
>De standaardwaarde is `NO` en deze optie laadt alleen advertenties vanaf het huidige actieve punt.

Bijvoorbeeld:

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
 
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
adMetadata.zoneId = <ZoneId>; 
adMetadata.domain = <Domain>; 
 
// Enable DVR Ads by setting to YES the enableDVRAds property on PTAdMetadata  
// (PTAuditudeMetadata is a subclass of PTAdMetadata)  
adMetadata.enableDVRAds = YES; 
 
[metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
 
//Create PTMediaPlayerItem with the previously prepared metadata    
playerItem = [[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata]; 
```
