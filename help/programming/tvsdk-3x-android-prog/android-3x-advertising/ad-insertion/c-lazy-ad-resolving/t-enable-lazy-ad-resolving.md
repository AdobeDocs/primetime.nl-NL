---
description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen via het bestaande mechanisme voor Lazy en oplossen (de functie Oplossen via Lazy en oplossen is standaard uitgeschakeld).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen via het bestaande mechanisme voor Lazy en oplossen (de functie Oplossen via Lazy en oplossen is standaard uitgeschakeld).
seo-title: Lozy en oplossen inschakelen
title: Lozy en oplossen inschakelen
uuid: 91884eea-a622-4f5d-b6a8-36bb0050ba1d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Lozy en oplossen inschakelen {#enable-lazy-ad-resolving}

U kunt de functie Oplossen via Lazy en laden in- of uitschakelen via het bestaande mechanisme voor Lazy en oplossen (de functie Oplossen via Lazy en oplossen is standaard uitgeschakeld).

U kunt Lazy Ad oplossen in- of uitschakelen door [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) aan te roepen met waar of onwaar.

* Gebruik de methoden Boolean *hasDelayAdLoading* en *setDelayAdLoading* in AdvertisingMetadata om de timing van de advertentiesolutie en de plaatsing van advertenties op de tijdlijn te bepalen:

   * Als *hasDelayAdLoading* false retourneert, wacht TVSDK totdat alle advertenties zijn opgelost en geplaatst voordat wordt overgeschakeld naar de status PREPARED.
   * Als *hasDelayAdLoading* true retourneert, lost TVSDK alleen de initiële advertenties en overgangen naar de status PREPARED op.

      * De resterende advertenties worden opgelost en tijdens het afspelen geplaatst.
   * Als *hasPreroll *of *hasLivePreroll* false retourneert, gaat TVSDK ervan uit dat er geen preroll-advertentie is en wordt het afspelen van de inhoud direct gestart. Deze zijn standaard ingesteld op true.


**API&#39;s die relevant zijn voor luie advertentie-resolutie:**

```
Class:    com.adobe.mediacore.metadata.AdvertisingMetadata 
Methods: 
    public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
    public final void setDelayAdLoading() // Enable or disable Lazy Ad Resolving 
    public final void setDelayAdLoadingTolerance() // Sets the Lazy Ad Resolving Tolerance level.  This value is added to the BufferControlParameters::playBufferTime and the content's EXT-X-TARGETDURATION to determine when ad breaks should resolve 
    public final double getDelayAdLoadingTolerance() // Gets the Lazy Ad Resolving Tolerance level 
    public final boolean hasPreroll() // Check for existence of pre-roll ads 
    public final void setPreroll() // Set pre-roll true or false 
    public final boolean hasLivePreroll() // Check for live pre-roll ads 
    public final void setLivePreroll() // Set live pre-roll true or false

Class:     com.adobe.mediacore.timeline.TimelineMarker 
Methods: 
    public double getDuration() // Returns the current duration of the TimelineMarker.  This will be zero if the ad break has not yet resolved. 
    public Placement.Type getPlacementType() // Returns whether
```

Als u advertenties nauwkeurig wilt spiegelen als aanwijzingen op een scrubbalk, luistert u naar de `TimelineEvent`gebeurtenis en tekent u de scrubbalk telkens wanneer u deze gebeurtenis ontvangt.

Wanneer Lazy Ad Resolving voor VOD stromen wordt toegelaten, worden alle ad onderbrekingen geplaatst op de chronologie, nochtans, zullen veel van de ad onderbrekingen nog niet worden opgelost. De toepassing kan bepalen of deze markeringen al dan niet moeten worden getekend door de `TimelineMarker::getDuration()`muis te bedienen. Als de waarde groter is dan nul, zijn de advertenties in het ad-einde opgelost.

TVSDK verzendt deze gebeurtenis wanneer een ad-einde is opgelost en ook wanneer de speler overschakelt naar de status PREPARED.

```
mediaPlayer.addEventListener(MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
/** 
* ... 
*/ 
public void onTimelineUpdated(TimelineEvent event) { 
for (PlaybackManagerEventListener listener : eventListeners) { 
  listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
}
```
