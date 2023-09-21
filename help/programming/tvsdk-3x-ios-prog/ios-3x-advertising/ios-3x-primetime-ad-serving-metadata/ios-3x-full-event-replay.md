---
description: TVSDK ondersteunt het omzetten en invoegen van advertenties voor VOD en live/lineaire streams.
title: Metagegevens van primetime en server
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Advertenties inschakelen bij volledig afspelen van gebeurtenissen {#section_6016E1DAF03645C8A8388D03C6AB7571}

FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.

Voor live-inhoud gebruikt TVSDK de metagegevens/aanwijzingen in het manifest om te bepalen waar advertenties moeten worden geplaatst. Soms lijkt het echter wel of levende/lineaire inhoud op VOD-inhoud lijkt. Wanneer de actieve inhoud bijvoorbeeld is voltooid, kan een `EXT-X-ENDLIST` -tag wordt toegevoegd aan het live-manifest. Voor HLS, `EXT-X-ENDLIST` -tag betekent dat de stream een VOD-stream is. TVSDK kan deze stream niet automatisch onderscheiden van een normale VOD-stream om advertenties correct in te voegen.

Uw toepassing moet TVSDK laten weten of de inhoud live is of VOD door de `PTAdSignalingMode`.

Voor een FER-stream moet de Adobe Primetime en de beslissingsserver geen lijst met ad-hoconderbrekingen opgeven die op de tijdlijn moeten worden ingevoegd voordat het afspelen wordt gestart. Dit is het gebruikelijke proces voor VOD-inhoud. In plaats daarvan, door een verschillende signalerende wijze te specificeren, leest TVSDK alle richtsnoerpunten van FER manifest en gaat naar de advertentieserver voor elk richtsnoerpunt om een advertentieonderbreking te verzoeken. Dit proces lijkt op live/DVR-inhoud.

Naast elke aanvraag die aan een actiepunt is gekoppeld, doet TVSDK een aanvullende advertentieaanvraag voor pre-roll-advertenties.

1. Van een externe bron, zoals vCMS, verkrijg de signalerende wijze die zou moeten worden gebruikt.
1. Maak de metagegevens die betrekking hebben op reclame.
1. Als het standaardgedrag moet worden overschreven, geeft u de opdracht `PTAdSignalingMode` door `PTAdMetadata.signalingMode`.

   De geldige waarden zijn `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`, en `PTAdSignalingModeServerMap`.

   U moet de ad signalerende wijze plaatsen alvorens te roepen `prepareToPlay`. Nadat TVSDK de bewerkingen voor advertenties heeft opgelost en op de tijdlijn heeft geplaatst, worden wijzigingen in de modus voor advertenties genegeerd. Stel de modus in wanneer u de advertentiemetagegevens voor de bron maakt.

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
