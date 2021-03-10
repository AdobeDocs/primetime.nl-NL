---
description: TVSDK ondersteunt het omzetten en invoegen van advertenties voor VOD en live/lineaire streams.
title: Metagegevens van primetime en server
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Overzicht {#primetime-ad-server-metadata-overview}

TVSDK ondersteunt het omzetten en invoegen van advertenties voor VOD en live/lineaire streams.

## Vereiste

Geef de volgende metagegevens op voordat u reclame in uw video-inhoud kunt opnemen:

* A `mediaID`, die de specifieke inhoud identificeert die moet worden afgespeeld.
* Uw `zoneID`, die uw bedrijf of website identificeert.
* Uw advertentieserverdomein, dat het domein van uw toegewezen advertentieserver specificeert.
* Andere doelparameters.

## Metagegevens van primetime en server instellen {#section_86C4A3B2DF124770B9B7FD2511394313}

Uw toepassing moet TVSDK de vereiste `PTAuditudeMetadata` informatie verstrekken om met de advertentieserver te verbinden.

De metagegevens van de advertentieserver instellen:

1. Maak een instantie van [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) en stel de eigenschappen ervan in.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Stel de `PTAuditudeMetadata`-instantie in als metagegevens voor de huidige `PTMediaPlayerItem`-metagegevens met `PTAdResolvingMetadataKey`.

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   Hier volgt een voorbeeld:

   ```
   PTMetadata *metadata = [self createMetadata]; 
   PTMediaPlayerItem *item =  
     [[[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease]; 
   
   - (PTMetadata *) createMetadata { 
       PTMetadata* metadata = [[[PTMetadata alloc] init] autorelease]; 
   
       PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
       adMetadata.zoneId = yourZoneID; 
       adMetadata.domain = yourAdServerDomain; 
   
       [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
       return metadata; 
   }
   ```
