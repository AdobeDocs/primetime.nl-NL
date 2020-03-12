---
description: U kunt opgeven of het afspelen is toegestaan voordat alle advertenties zijn geladen en in de tijdlijn zijn geplaatst. Als u het afspelen op deze manier start, heeft een viewer sneller toegang tot de hoofdinhoud. Deze functie is alleen van toepassing op levende DVR en werkt niet aan VOD-activa.
seo-description: U kunt opgeven of het afspelen is toegestaan voordat alle advertenties zijn geladen en in de tijdlijn zijn geplaatst. Als u het afspelen op deze manier start, heeft een viewer sneller toegang tot de hoofdinhoud. Deze functie is alleen van toepassing op levende DVR en werkt niet aan VOD-activa.
seo-title: Lazy en laden inschakelen
title: Lazy en laden inschakelen
uuid: ac7c8801-7fa2-4f17-b79c-c603b3236948
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Lazy en laden inschakelen{#enable-lazy-ad-loading}

U kunt opgeven of het afspelen is toegestaan voordat alle advertenties zijn geladen en in de tijdlijn zijn geplaatst. Als u het afspelen op deze manier start, heeft een viewer sneller toegang tot de hoofdinhoud. Deze functie is alleen van toepassing op levende DVR en werkt niet aan VOD-activa.

1. Gebruik de eigenschap Boolean `delayAdLoading` in `AdvertisingMetadata`.

   * Indien onwaar wacht TVSDK tot alle advertenties zijn opgelost en geplaatst voordat wordt overgeschakeld naar de status PREPARED. Deze waarde is standaard false.
   * Indien waar (true), lost TVSDK alleen de initiële advertenties en overgangen naar de status PREPARED op. De resterende advertenties worden opgelost en tijdens het afspelen geplaatst.

1. Als u vertraagd laden en laden ook wilt activeren met Adobe Primetime en beslissen, stelt u dit in op `true` wanneer u een document maakt `AuditudeSettings`.

   De `AuditudeSettings` klasse overerft deze eigenschap van `AdvertisingMetadata`, maar neemt de huidige waarde niet over.

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings(); 
   auditudeSettings.mediaId = ... 
   auditudeSettings.zoneId = ... 
   auditudeSettings.delayAdLoading = true;
   ```

1. Als u advertenties nauwkeurig wilt spiegelen als aanwijzingen op een scrubbalk, luistert u naar de `TimelineEvent`knop. `TIMELINE_UPDATED` en teken de scrubbalk telkens opnieuw wanneer u deze gebeurtenis ontvangt.

   Wanneer VoD-streams vertraagd en geladen gebruiken, worden niet alle advertenties op de tijdlijn geplaatst wanneer de speler de status PREPARED inschakelt. U moet daarom de scrubbalk expliciet opnieuw tekenen.

   TVSDK optimaliseert de verzending van deze gebeurtenis om het aantal keren dat u de scrubbalk opnieuw moet tekenen, te minimaliseren; Het aantal tijdlijngebeurtenissen houdt daarom geen verband met het aantal ad-hocpauzes dat op de tijdlijn moet worden geplaatst. Als u bijvoorbeeld vijf ad-einden hebt, krijgt u mogelijk niet precies vijf gebeurtenissen.

   ```
   mediaPlayer.addEventListener(TimelineEvent.TIMELINE_UPDATED, onTimelineUpdated); 
   // ... 
   function onTimelineUpdated(event:TimelineEvent):void { 
       // get markers 
       var markers:Vector.<TimelineMarker> = event.timeline.timelineMarkers; 
       drawMarkers(markers); 
   } 
   ```

