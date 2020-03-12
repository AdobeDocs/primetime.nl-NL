---
description: Met gebeurtenishandlers kunt u reageren op TVSDK-gebeurtenissen.
seo-description: Met gebeurtenishandlers kunt u reageren op TVSDK-gebeurtenissen.
seo-title: Gebeurtenislisteners en callbacks implementeren
title: Gebeurtenislisteners en callbacks implementeren
uuid: bb1980f3-340b-4d36-ae7e-c9fc1d145233
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Gebeurtenislisteners en callbacks implementeren {#implement-event-listeners-and-callbacks}

Met gebeurtenishandlers kunt u reageren op TVSDK-gebeurtenissen.

Wanneer een gebeurtenis plaatsvindt, roept het gebeurtenismechanisme van TVSDK uw geregistreerde gebeurtenismanager aan, die het de gebeurtenisinformatie overgaat.

TVSDK definieert listeners als openbare interne interfaces binnen de `MediaPlayer` interface.

Uw toepassing moet gebeurtenislisteners implementeren voor alle TVSDK-gebeurtenissen die van invloed zijn op uw toepassing.

1. Bepaal op welke gebeurtenissen uw toepassing moet letten.

   * Vereiste gebeurtenissen: Luister naar alle afspeelgebeurtenissen.

      >[!IMPORTANT]
      >
      >Luister naar de gebeurtenis over statuswijziging die optreedt wanneer de status van de speler verandert op een manier die u moet weten. De informatie die wordt verschaft, bevat fouten die mogelijk van invloed zijn op de volgende taken van de speler.

   * Voor andere gebeurtenissen, afhankelijk van uw toepassing, zie gebeurtenissen-samenvatting.

1. Een gebeurtenislistener voor elke gebeurtenis implementeren en toevoegen.

   >[!NOTE]
   >
   >Voor de meeste gebeurtenissen geeft TVSDK argumenten door aan de gebeurtenislisteners. Dergelijke waarden bieden informatie over de gebeurtenis die u kan helpen bepalen wat u moet doen. De `MediaPlayerEvent` opsomming bevat een lijst met alle gebeurtenissen die worden `MediaPlayer` verzonden. Zie voor meer informatie de samenvatting van gebeurtenissen.

   Als `mPlayer` dit bijvoorbeeld een geval van `MediaPlayer`is, kunt u hier een gebeurtenislistener toevoegen en structureren:

   ```java
   mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() { 
       @Override 
       public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
           event.getMetadata(); 
           if (event.getMetadata() != null) {/* Do something */} 
           if (event.getStatus() == MediaPlayerStatus.IDLE) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.INITIALIZED) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.PREPARED) {/* Do something */} 
       } 
   }); 
   ```

## Volgorde van afspeelgebeurtenissen {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

De volgende voorbeelden laten de volgorde zien van bepaalde gebeurtenissen die plaatsvinden tijdens het afspelen.

Wanneer het laden van een mediabron is geslaagd, is de volgorde van gebeurtenissen: `MediaPlayer.replaceCurrentResource`

1. `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Laad de mediabron in de hoofdthread. Als u een mediabron in een achtergrondthread laadt, kan deze bewerking of volgende bewerkingen een fout genereren, zoals `MediaPlayerException`en afsluiten.

Wanneer u het afspelen voorbereidt, is de volgorde van gebeurtenissen: `MediaPlayer.prepareToPlay`

1. `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` als er advertenties zijn ingevoegd.
1. `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.PREPARED`

Voor live/lineaire streams, tijdens het afspelen terwijl het afspeelvenster vordert en er extra mogelijkheden worden opgelost, is de volgorde van gebeurtenissen:

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` als er advertenties zijn ingevoegd

## Volgorde van reclameevenementen {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Wanneer uw afspelen advertenties bevat, verzendt TVSDK gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. Uw speler kan handelingen implementeren op basis van gebeurtenissen binnen de verwachte volgorde.

Bij het afspelen van advertenties is de volgorde van gebeurtenissen:

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

De volgende gebeurtenissen worden verzonden voor elke advertentie binnen het ad-einde:

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

In het volgende voorbeeld ziet u een doorsnee progressie van gebeurtenissen voor het afspelen van advertenties:

```
mediaPlayer.addEventListener(MediaPlayerEvent.AD_RESOLUTION_COMPLETE, new AdResolutionCompleteEventListener() { 
        @Override 
        public void onAdResolutionComplete() { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_START, new AdBreakStartedEventListener() { 
         @Override 
        public void onAdBreakStarted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_START, new AdStartedEventListener() { 
         @Override 
        public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_PROGRESS, new AdProgressEventListener() { 
         @Override 
         public void onAdProgress(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_COMPLETE, new AdCompletedEventListener() { 
         @Override 
         public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_COMPLETE, new AdBreakCompletedEventListener() { 
         @Override 
         public void onAdBreakCompleted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
Below event is for tracking ad clicks. 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_CLICK, new AdClickedEventListener() { 
         @Override 
         public void onAdClicked(AdClickEvent adClickEvent) { ... } 
    });
```

## Volgorde van DRM-gebeurtenissen {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen. Uw speler kan als reactie op deze gebeurtenissen acties implementeren.

Luister naar gebeurtenissen als u een melding wilt ontvangen over alle DRM-gerelateerde gebeurtenissen `MediaPlayerEvent.DRM_METADATA`. TVSDK verzendt aanvullende DRM-gebeurtenissen via de `DRMManager` klasse.

## Volgorde van loader-gebeurtenissen {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK wordt verzonden `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` wanneer loader-gebeurtenissen optreden.