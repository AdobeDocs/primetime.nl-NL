---
description: Met gebeurtenishandlers kan TVSDK reageren op gebeurtenissen.
seo-description: Met gebeurtenishandlers kan TVSDK reageren op gebeurtenissen.
seo-title: Gebeurtenislisteners en callbacks implementeren
title: Gebeurtenislisteners en callbacks implementeren
uuid: 6b7859a4-55f9-48b1-b1f1-7b79bc92610a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Gebeurtenislisteners en callbacks implementeren{#implement-event-listeners-and-callbacks}

Met gebeurtenishandlers kan TVSDK reageren op gebeurtenissen.

Wanneer een gebeurtenis voorkomt, roept het gebeurtenismechanisme van TVSDK uw geregistreerde gebeurtenismanager en gaat de gebeurtenisinformatie tot de manager over.

TVSDK definieert listeners als openbare interne interfaces in de `MediaPlayer` interface.

Uw toepassing moet gebeurtenislisteners implementeren voor TVSDK-gebeurtenissen die van invloed zijn op uw toepassing.

Zie Core Video Playback bijhouden voor een volledige lijst met gebeurtenissen voor videoanalyse.

1. Bepaal voor welke gebeurtenissen uw toepassing moet luisteren.

   * **Vereiste gebeurtenissen**: Luister naar alle afspeelgebeurtenissen.

      >[!IMPORTANT]
      >
      >De afspeelgebeurtenis `onStateChanged` geeft de spelerstatus aan, inclusief fouten. Een van de statussen heeft mogelijk invloed op de volgende stap van de speler

   * **Andere gebeurtenissen**: Optioneel, afhankelijk van uw toepassing.

      Bijvoorbeeld, als u reclame in uw playback opneemt, voer de callbacks AdPlaybackEventListener uit.

1. Implementeer gebeurtenislisteners voor elke gebeurtenis.

   TVSDK retourneert parameterwaarden aan uw callbacks van de gebeurtenislistener. Deze waarden bieden relevante informatie over de gebeurtenis die u in de listeners kunt gebruiken om de juiste handelingen uit te voeren.

   `MediaPlayer.EventListener` maakt een lijst van alle callback interfaces. Elke interface toont de callback naam en de parameters die voor elke gebeurtenis zijn teruggekeerd.

   Bijvoorbeeld:

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. Registreer de callback-listeners met het `MediaPlayer` object `MediaPlayer.addEventListener`.

   ```
   mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, 
    new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onStateChanged( 
    MediaPlayer.PlayerState state, 
    MediaPlayerNotification notification) {...} 
   }
   ```

## Volgorde van afspeelgebeurtenissen {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK verzendt gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

In de volgende voorbeelden wordt de volgorde van bepaalde gebeurtenissen getoond, waaronder afspeelgebeurtenissen.

* Wanneer het laden van een mediabron is geslaagd, is de volgorde van gebeurtenissen: `MediaPlayer.replaceCurrentResource`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` met status `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` met status `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>Laad de mediabron in de hoofdthread. Als u een mediabron laadt in een achtergrondthread, kan deze bewerking of volgende TVSDK-bewerkingen (of beide) een fout veroorzaken (bijvoorbeeld `IllegalStateException`) en afsluiten.

* Wanneer u het afspelen voorbereidt, is de volgorde van gebeurtenissen: `MediaPlayer.prepareToPlay`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` met status `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` als er advertenties zijn ingevoegd.
1. `MediaPlayer.PlaybackEventListener.onStateChanged` met status `MediaPlayerStatus.PREPARED`

* Voor live/lineaire streams, tijdens het afspelen terwijl het afspeelvenster vordert en er extra mogelijkheden worden opgelost, is de volgorde van gebeurtenissen:

1. `MediaPlayer.PlaybackEventListener.onUpdated`
1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` als er advertenties zijn ingevoegd
1. `MediaPlayerItemEvent.ITEM_UPDATED`
1. `TimelineEvent.TIMELINE_UPDATED` als er advertenties zijn ingevoegd

In het volgende voorbeeld wordt een typische progressie van gebeurtenissen getoond:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK,  
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() {...} 
    @Override 
    public void onUpdated() {...} 
    @Override 
    public void onPlayStart() {...} 
    @Override 
    public void onPlayComplete() {...} 
    @Override 
    public void onSizeAvailable(long height, long width) {...} 
    @Override 
    public void onStateChanged(MediaPlayer.PlayerState state,  
      MediaPlayerNotification notification) {...} 
});
```

## Volgorde van reclameevenementen {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

Wanneer uw afspelen advertenties bevat, verzendt TVSDK gebeurtenissen/meldingen in de over het algemeen verwachte reeksen. De speler kan handelingen implementeren op basis van gebeurtenissen in de verwachte volgorde.

Bij het afspelen van advertenties is de volgorde van gebeurtenissen:

* `AdPlaybackEventListener.onAdBreakStart`
* Het volgende wordt verzonden voor elke advertentie in het ad-einde:

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (meerdere keren tijdens het afspelen van een advertentie)
   * `AdPlaybackEventListener.onAdClick` (voor elke klik)
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

In het volgende voorbeeld ziet u een doorsnee progressie van gebeurtenissen voor het afspelen van advertenties:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

Bij het afspelen van advertenties is de volgorde van gebeurtenissen:

* `AdPlaybackEventListener.onAdBreakStart`
* Het volgende wordt verzonden voor elke advertentie in het ad-einde:

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` (meerdere keren tijdens het afspelen van een advertentie)
   * `AdPlaybackEventListener.onAdClick` (voor elke klik)
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

In het volgende voorbeeld ziet u een doorsnee progressie van gebeurtenissen voor het afspelen van advertenties:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

## QoS-gebeurtenissen {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDK verstuurt QoS-gebeurtenissen (quality of service) om uw toepassing op de hoogte te stellen van gebeurtenissen die de berekening van QoS-statistieken kunnen beïnvloeden, zoals het bufferen en zoeken van gebeurtenissen.

In het volgende voorbeeld wordt een typische progressie van deze gebeurtenissen getoond:

```java
mediaPlayer.addEventListener(MediaPlayer.Event.QOS,  
  new MediaPlayer.QOSEventListener(){ 
    //For buffering activity 
    @Override 
    public void onBufferStart() 
    @Override 
    public void onBufferComplete() 
    // For seeking 
    @Override 
    public void onSeekStart() 
    @Override 
    public void onSeekComplete(long adjustedTime) 
    @Override 
    public void onLoadComplete (MediaPlayerItem mediaplayeritem) 
    @Override 
    public void onLoadInfo(LoadInfo loadInfo) 
    @Override 
    public void onOperationFailed(MediaPlayerNotification.Warning warning) 
});
```

## DRM-gebeurtenissen {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK verzendt DRM-gebeurtenissen (Digital Rights Management) als reactie op DRM-gerelateerde bewerkingen, zoals wanneer nieuwe DRM-metagegevens beschikbaar komen. Uw speler kan als reactie op deze gebeurtenissen acties implementeren.

Luister naar gebeurtenissen als u een melding wilt ontvangen over alle DRM-gerelateerde gebeurtenissen `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`. TVSDK verzendt aanvullende DRM-gebeurtenissen via de `DRMManager` klasse.

In het volgende voorbeeld wordt een gemiddelde progressie getoond:

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## Gebeurtenissen van Loader {#section_5638F8EDACCE422A9425187484D39DCC}

Uw speler kan handelingen implementeren op basis van de volgende gebeurtenissen:

| Gebeurtenis | Betekenis |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | Het laden van mediabronnen is voltooid. |
| `onError` | Er is een probleem opgetreden bij het laden van mediabronnen. |

