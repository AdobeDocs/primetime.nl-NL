---
description: Met gebeurtenishandlers kunt u reageren op TVSDK-gebeurtenissen.
title: Gebeurtenislisteners en callbacks implementeren
exl-id: c8825a6c-3d48-412f-81f5-542c7731a122
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

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
   >Voor de meeste gebeurtenissen geeft TVSDK argumenten door aan de gebeurtenislisteners. Dergelijke waarden bieden informatie over de gebeurtenis die u kan helpen bepalen wat u moet doen. De `MediaPlayerEvent` opsomming bevat alle gebeurtenissen die `MediaPlayer` verzenden. Zie voor meer informatie de samenvatting van gebeurtenissen.

   Als `mPlayer` is een instantie van `MediaPlayer`Hieronder ziet u hoe u een gebeurtenislistener kunt toevoegen en structureren:

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

Wanneer het laden van een mediabron is voltooid `MediaPlayer.replaceCurrentResource`De volgorde van gebeurtenissen is:

1. `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` met status `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>Laad de mediabron in de hoofdthread. Als u een mediabron laadt in een achtergrondthread, kan deze bewerking of volgende bewerkingen een fout veroorzaken, zoals `MediaPlayerException`en afsluiten.

Wanneer u het afspelen voorbereidt via `MediaPlayer.prepareToPlay`De volgorde van gebeurtenissen is:

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

Als u op de hoogte wilt worden gesteld van alle DRM-gerelateerde gebeurtenissen, luistert u naar `MediaPlayerEvent.DRM_METADATA`. TVSDK verzendt aanvullende DRM-gebeurtenissen via de `DRMManager` klasse.

## Volgorde van loader-gebeurtenissen {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK verzendt `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` wanneer loader-gebeurtenissen optreden.
