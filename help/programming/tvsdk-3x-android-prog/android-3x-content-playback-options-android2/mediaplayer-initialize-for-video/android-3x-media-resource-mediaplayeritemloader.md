---
description: Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.
title: Een mediabron laden met MediaPlayerItemLoader
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Een mediabron laden met MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.

De `MediaPlayerItemLoader` de klasse helpt u een media middel voor de huidige `MediaPlayerItem` zonder een weergave te koppelen aan een `MediaPlayer` -instantie, die hardwarebronnen voor videodecodering zou toewijzen. Extra stappen zijn nodig voor met DRM beveiligde inhoud, maar deze handleiding bevat geen beschrijving van de stappen.

>[!IMPORTANT]
>
>TVSDK biedt geen ondersteuning voor één `QoSProvider` werken met beide `itemLoader` en `MediaPlayer`. Als uw toepassing Direct On gebruikt, moet de toepassing twee `QoS` instanties en beheert beide instanties voor de informatie. Zie [Direct aan](../../android-3x-content-playback-options-android2/buffering-configuration/android-3x-instant-on.md) voor meer informatie .

1. Een instantie maken van `MediaPlayerItemLoader`.

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
   
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
   
           public void onBufferingBegin() { 
               //Do something 
           } 
   
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       }); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   } 
   ```

   >[!TIP]
   >
   >Een aparte instantie maken van `MediaPlayerItemLoader` voor elke bron. Gebruik er geen `MediaPlayerItemLoader` -instantie om meerdere bronnen te laden.

1. Implementeer de `ItemLoaderListener` klasse die meldingen van de `MediaPlayerItemLoader` -instantie.

   ```java
   private MediaPlayerItemLoader createLoader() { 
       MediaPlayerItemLoader itemLoader =   
         new MediaPlayerItemLoader(this, new MediaPlayerItemLoader.LoaderListener() { 
           public void onError(PSDKErrorCode mediaErrorCode, String description) { 
               //Do something 
           } 
           public void onLoadComplete(MediaPlayerItem playerItem) { 
               loader.prepareBuffer(); 
           } 
           public void onBufferingBegin() { 
               //Do something 
           } 
           public void onBufferPrepared() { 
               mPlayer.reset(); 
           }  
       } ); 
   
       itemLoader.setKeepRebufferingForLive(true); 
       return itemLoader; 
   }
   ```

   In de `onLoadComplete()` callback, doe één van het volgende:

   * Zorg ervoor dat alles wat buffering kan beïnvloeden, bijvoorbeeld het selecteren van WebVTT- of audiotracks, volledig is en aanroept `prepareBuffer()` om direct te profiteren van.
   * Het item aan het `MediaPlayer` instantie gebruiken `replaceCurrentItem()`.

   Als u `prepareBuffer()`ontvangt u de BUFFER_PREPARED-gebeurtenis in uw `onBufferPrepared` handler wanneer de bereiding is voltooid.
1. Bellen `load` op de `MediaPlayerItemLoader` instantie en geef de te laden bron en eventueel de inhoud-id door, en een `MediaPlayerItemConfig` -instantie.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Als u vanaf een ander punt dan het begin van de stream wilt bufferen, roept u `prepareBuffer()` met de positie (in milliseconden) waarop wordt gebufferd.
1. Gebruik de `replaceCurrentItem()` en `play()` methoden `MediaPlayer` om vanaf dat punt af te spelen.
1. Wacht op nutteloze status en vraag `replaceCurrentItem`.
1. Het item afspelen.

   * Als het item is geladen maar niet is gebufferd:

      1. Wacht op geïnitialiseerde status.
      1. Bellen `prepareToPlay()`.
      1. Wacht op de status PREPARED.
      1. Bellen `play()`.

   * Als het item is gebufferd:

      1. Wacht op de gebeurtenis die in de buffer is voorbereid.
      1. Bellen `play()`.
