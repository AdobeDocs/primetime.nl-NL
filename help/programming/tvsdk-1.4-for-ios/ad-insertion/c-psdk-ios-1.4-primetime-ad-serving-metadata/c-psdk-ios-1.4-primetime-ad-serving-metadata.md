---
description: TVSDK ondersteunt het omzetten en invoegen van advertenties voor VOD en live/lineaire streams.
seo-description: TVSDK ondersteunt het omzetten en invoegen van advertenties voor VOD en live/lineaire streams.
seo-title: Metagegevens van primetime en server
title: Metagegevens van primetime en server
uuid: 314f14c0-4da4-4da6-96f9-5a5ffea22a99
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# Overzicht {#primetime-ad-server-metadata-overview}

TVSDK ondersteunt het omzetten en invoegen van advertenties voor VOD en live/lineaire streams.

>[!NOTE]
>
>Geef de volgende metagegevens op voordat u reclame in uw video-inhoud kunt opnemen:
>
>* A `mediaID`, dat de specifieke inhoud identificeert die moet worden afgespeeld.
>* Uw `zoneID`, die uw bedrijf of website identificeert.
>* Uw advertentieserverdomein, dat het domein van uw toegewezen advertentieserver specificeert.
>* Andere doelparameters.

>



## Metagegevens van primetime en server instellen {#section_86C4A3B2DF124770B9B7FD2511394313}

Uw toepassing moet TVSDK de vereiste `PTAuditudeMetadata` informatie verstrekken om verbinding te maken met de advertentieserver.

De metagegevens van de advertentieserver instellen:

1. Maak een instantie van [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) en stel de eigenschappen ervan in.

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. Stel de `PTAuditudeMetadata` instantie in als metagegevens voor de huidige `PTMediaPlayerItem` metagegevens door deze te gebruiken `PTAdResolvingMetadataKey`.

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

## Advertenties inschakelen bij volledig afspelen van gebeurtenissen {#section_6016E1DAF03645C8A8388D03C6AB7571}

FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.

Voor live-inhoud gebruikt TVSDK de metagegevens/aanwijzingen in het manifest om te bepalen waar advertenties moeten worden geplaatst. Soms lijkt het echter wel of levende/lineaire inhoud op VOD-inhoud lijkt. Wanneer de actieve inhoud bijvoorbeeld is voltooid, wordt een `EXT-X-ENDLIST` tag toegevoegd aan het live manifest. Voor HLS betekent de `EXT-X-ENDLIST` tag dat de stream een VOD-stream is. TVSDK kan deze stream niet automatisch onderscheiden van een normale VOD-stream om advertenties correct in te voegen.

Uw toepassing moet TVSDK laten weten of de inhoud live of VOD is door de `PTAdSignalingMode`inhoud op te geven.

Voor een FER-stream moet de Adobe Primetime en de beslissingsserver geen lijst met ad-hoconderbrekingen opgeven die op de tijdlijn moeten worden ingevoegd voordat het afspelen wordt gestart. Dit is het gebruikelijke proces voor VOD-inhoud. In plaats daarvan, door een verschillende signalerende wijze te specificeren, leest TVSDK alle richtsnoerpunten van FER manifest en gaat naar de advertentieserver voor elk richtsnoerpunt om een advertentieonderbreking te verzoeken. Dit proces lijkt op live/DVR-inhoud.

Naast elke aanvraag die aan een actiepunt is gekoppeld, doet TVSDK een aanvullende advertentieaanvraag voor pre-roll-advertenties.

1. Van een externe bron, zoals vCMS, verkrijg de signalerende wijze die zou moeten worden gebruikt.
1. Maak de metagegevens die betrekking hebben op reclame.
1. Als het standaardgedrag moet worden beschreven, specificeer `PTAdSignalingMode` door te gebruiken `PTAdMetadata.signalingMode`.

   De geldige waarden zijn `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`en `PTAdSignalingModeServerMap`.

   U moet de advertentie signalerende wijze plaatsen alvorens `prepareToPlay`te roepen. Nadat TVSDK de bewerkingen voor advertenties heeft opgelost en op de tijdlijn heeft geplaatst, worden wijzigingen in de modus voor advertenties genegeerd. Stel de modus in wanneer u de advertentiemetagegevens voor de bron maakt.

1. Doorgaan met afspelen.

   ```
      PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.zoneId = your-auditude-zone-id; 
   adMetadata.domain = @"your-auditude-domain"; 
   //adMetadata.enableDVRAds = YES; // FOR LIVE DVR case 
   //adMetadata.signalingMode = PTAdSignalingModeManifestCues;  
   // FOR VOD FER case 
   NSMutableDictionary *targetingParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [targetingParameters setValue:@"ipad" forKey:@"device"]; 
   [targetingParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.targetingParameters = targetingParameters; 
   NSMutableDictionary *customParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [customParameters setValue:@"your-media-id" forKey:@"NW_ID"]; 
   [customParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.customParameters = customParameters; 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   ```

