---
description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en oplossen (Lazy Ad Resolving is standaard ingeschakeld).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en oplossen (Lazy Ad Resolving is standaard ingeschakeld).
seo-title: Lozy en oplossen inschakelen
title: Lozy en oplossen inschakelen
uuid: a084ee0b-53af-4600-91f6-d30ccc89699d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Lozy en oplossen inschakelen {#enable-lazy-ad-resolving}

U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en oplossen (Lazy Ad Resolving is standaard ingeschakeld).

U kunt Lazy Ad oplossen in- of uitschakelen door [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) aan te roepen met `true` of `false`.

1. Gebruik de Booleaanse waarde `hasDelayAdLoading` en de `setDelayAdLoading` methoden in `AdvertisingMetadata` om de tijdinstelling van de resolutie en de plaatsing van de advertenties op de tijdlijn te bepalen:

   * Als de waarde false `hasDelayAdLoading` wordt geretourneerd, wacht TVSDK totdat alle advertenties zijn opgelost en worden geplaatst voordat wordt overgeschakeld naar de status PREPARED.
   * Als de waarde true wordt `hasDelayAdLoading` geretourneerd, worden alleen de eerste advertenties en overgangen naar de status PREPARED opgelost. De resterende advertenties worden opgelost en tijdens het afspelen geplaatst.
   * Als `hasPreroll` of als deze false `hasLivePreroll` retourneren, gaat TVSDK ervan uit dat er geen preroll-advertentie is en wordt het afspelen van de inhoud direct gestart. Deze standaardinstelling is true.

      API&#39;s die relevant zijn voor luie advertentie-resolutie:

      ```
      Class: 
         com.adobe.mediacore.metadata.AdvertisingMetadata 
      
      Methods: 
      […] 
          public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
          public final void setDelayAdLoading()    // Enable or disable Lazy Ad Resolving 
          public final boolean hasPreroll()        // Check for existence of pre-roll ads 
          public final void setPreroll()           // Set pre-roll true or false 
          public final boolean hasLivePreroll()    // Check for live pre-roll ads 
          public final void setLivePreroll()       // Set live pre-roll true or false 
      […]
      ```

1. Als u advertenties nauwkeurig wilt spiegelen als aanwijzingen op een scrubbalk, luistert u naar de `TimelineEvent` gebeurtenis en tekent u de scrubbalk telkens opnieuw wanneer u deze gebeurtenis ontvangt.

   Wanneer Lazy Ad Resolving voor VOD stromen wordt toegelaten, worden niet alle advertenties geplaatst op de chronologie wanneer uw speler de PREPARED staat ingaat, zodat moet uw speler uitdrukkelijk de scrub bar opnieuw trekken.

   TVSDK optimaliseert de verzending van deze gebeurtenis om het aantal keren dat u de scrubbalk opnieuw moet tekenen, te minimaliseren; Het aantal tijdlijngebeurtenissen houdt daarom geen verband met het aantal ad-hocpauzes dat op de tijdlijn moet worden geplaatst. Als u bijvoorbeeld vijf ad-einden hebt, krijgt u mogelijk niet precies vijf gebeurtenissen.

   ```java
   mediaPlayer.addEventListener 
       (MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
   /** 
    * ... 
    */ 
   public void onTimelineUpdated(TimelineEvent event) { 
   
       for (PlaybackManagerEventListener listener : eventListeners) { 
           listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
       } 
   } 
   ```

>Om te verifiëren of de Verlof en het Oplossen eigenschap wordt toegelaten of onbruikbaar gemaakt, vraag `AdvertisingMetadata.hasDelayAdLoading`. Een geretourneerde waarde van `true` houdt in dat Lazy Ad Resolving is ingeschakeld. `false` betekent dat de functie is uitgeschakeld.

