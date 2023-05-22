---
description: U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en laden (de functie Oplossen via Lazy en oplossen is standaard ingeschakeld).
keywords: Lazy;Adverteren;Advertentie laden;delayLoading
title: Lozy en oplossen inschakelen
exl-id: 4cd53ace-b0f5-4eef-93c3-644c2f48ce49
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Lozy en oplossen inschakelen {#enable-lazy-ad-resolving}

U kunt de functie Oplossen via Lazy en laden in- of uitschakelen met behulp van het bestaande mechanisme voor Lazy en laden (de functie Oplossen via Lazy en oplossen is standaard ingeschakeld).

U kunt het Oplossen van de Lazy en onbruikbaar maken door te roepen [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) with `true` of `false`.

1. De Booleaanse waarde gebruiken `hasDelayAdLoading` en `setDelayAdLoading` methoden in `AdvertisingMetadata` om de timing van de advertentiesolutie en de plaatsing van advertenties op de tijdlijn te bepalen:

   * Indien `hasDelayAdLoading` retourneert false. TVSDK wacht totdat alle advertenties zijn opgelost en geplaatst voordat naar de status PREPARED wordt overgeschakeld.
   * Indien `hasDelayAdLoading` retourneert true, lost TVSDK alleen de initiële advertenties en overgangen naar de status PREPARED op. De resterende advertenties worden opgelost en tijdens het afspelen geplaatst.
   * Wanneer `hasPreroll` of `hasLivePreroll` Retourneer false, TVSDK gaat ervan uit dat er geen preroll-advertentie is en start het afspelen van de inhoud direct. Deze standaardinstelling is true.

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

1. Als u advertenties nauwkeurig wilt spiegelen als aanwijzingen op een scrubbalk, luistert u naar de knop `TimelineEvent` en teken de scrubbalk telkens opnieuw wanneer u deze gebeurtenis ontvangt.

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

>Om te verifiëren of de luie en Oplossende eigenschap wordt toegelaten of onbruikbaar gemaakt, vraag `AdvertisingMetadata.hasDelayAdLoading`. Een geretourneerde waarde van `true` betekent dat Lazy Ad Resolving wordt toegelaten; `false` betekent dat de functie is uitgeschakeld.
