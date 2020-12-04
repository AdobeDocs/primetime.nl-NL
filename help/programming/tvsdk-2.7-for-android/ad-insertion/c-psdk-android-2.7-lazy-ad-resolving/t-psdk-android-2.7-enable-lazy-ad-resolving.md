---
description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en laden (de functie Oplossen via Lazy en oplossen is standaard ingeschakeld).
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en laden (de functie Oplossen via Lazy en oplossen is standaard ingeschakeld).
seo-title: Lozy en oplossen inschakelen
title: Lozy en oplossen inschakelen
uuid: a084ee0b-53af-4600-91f6-d30ccc89699d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# {#enable-lazy-ad-resolving} lui inschakelen en oplossen

U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en laden (de functie Oplossen via Lazy en oplossen is standaard ingeschakeld).

U kunt het oplossen van problemen in- of uitschakelen door [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) aan te roepen met `true` of `false`.

1. Gebruik de Booleaanse methoden `hasDelayAdLoading` en `setDelayAdLoading` in `AdvertisingMetadata` om de timing van de advertentiesolutie en de plaatsing van advertenties op de tijdlijn te bepalen:

   * Als `hasDelayAdLoading` false retourneert, wacht TVSDK totdat alle advertenties zijn opgelost en geplaatst voordat naar de status PREPARED wordt gegaan.
   * Als `hasDelayAdLoading` waar terugkeert, lost TVSDK slechts de aanvankelijke advertenties en de overgangen aan de PREPARED staat op. De resterende advertenties worden opgelost en tijdens het afspelen geplaatst.
   * Wanneer `hasPreroll` of `hasLivePreroll` false retourneert, gaat TVSDK ervan uit dat er geen preroll-advertentie is en wordt het afspelen van de inhoud direct gestart. Deze standaardinstelling is true.

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

1. Als u advertenties nauwkeurig wilt spiegelen als aanwijzingen op een scrubbalk, luistert u naar de gebeurtenis `TimelineEvent` en tekent u de scrubbalk telkens opnieuw wanneer u deze gebeurtenis ontvangt.

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

>Om te verifiëren of de luie en Oplossende eigenschap wordt toegelaten of onbruikbaar gemaakt, vraag `AdvertisingMetadata.hasDelayAdLoading`. Een geretourneerde waarde van `true` houdt in dat de optie Uitgestelde ad-oplossing is ingeschakeld; `false` betekent dat de functie is uitgeschakeld.

