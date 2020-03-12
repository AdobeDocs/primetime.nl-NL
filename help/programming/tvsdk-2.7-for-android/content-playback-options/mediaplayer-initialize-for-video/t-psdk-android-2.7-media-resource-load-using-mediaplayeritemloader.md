---
description: Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.
seo-description: Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.
seo-title: Een mediabron laden met MediaPlayerItemLoader
title: Een mediabron laden met MediaPlayerItemLoader
uuid: 43ca2470-1fd2-4f66-94fe-a12ed17b52d7
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Een mediabron laden met MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.

De `MediaPlayerItemLoader` klasse helpt u een media middel voor de stroom uit te wisselen `MediaPlayerItem` zonder een mening aan een `MediaPlayer` instantie vast te maken, die video decoderende hardwaremiddelen zou toewijzen. Extra stappen zijn nodig voor met DRM beveiligde inhoud, maar deze handleiding bevat geen beschrijving van de stappen.

>[!IMPORTANT]
>
>TVSDK biedt geen ondersteuning voor één functie `QoSProvider` voor zowel `itemLoader` als `MediaPlayer`. Als uw toepassing Instant On gebruikt, moet de toepassing twee `QoS` instanties onderhouden en beide instanties voor de informatie beheren. Zie [instant-on](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) voor meer informatie.

1. Maak een instantie van `MediaPlayerItemLoader`.

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
   >Maak een afzonderlijk exemplaar van `MediaPlayerItemLoader` elke bron. Gebruik geen enkele `MediaPlayerItemLoader` instantie om meerdere bronnen te laden.

1. Voer de `ItemLoaderListener` klasse uit om meldingen van de `MediaPlayerItemLoader` instantie te ontvangen.

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

   Voer in de `onLoadComplete()` callback een van de volgende handelingen uit:

   * Zorg ervoor dat om het even wat die het als buffer optreden, bijvoorbeeld, het selecteren van WebVTT of audiosporen zou kunnen beïnvloeden, volledig is en vraag `prepareBuffer()` om uit onmiddellijk voordeel te halen.
   * Koppel het item aan de `MediaPlayer` instantie met behulp van `replaceCurrentItem()`.
   Als u roept `prepareBuffer()`, ontvangt u de gebeurtenis BUFFER_PREPARED in uw `onBufferPrepared` manager wanneer de voorbereiding wordt gebeëindigd.

1. Vraag `load` op de `MediaPlayerItemLoader` instantie en ga het middel over om, en naar keuze inhoudsidentiteitskaart, en een `MediaPlayerItemConfig` instantie worden geladen.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Als u vanaf een ander punt dan het begin van de stream wilt bufferen, roept u `prepareBuffer()` met de positie (in milliseconden) aan waar het bufferen moet beginnen.
1. Gebruik de `replaceCurrentItem()` en de `play()` methoden om vanaf dat punt af `MediaPlayer` te spelen.
1. Wacht op nutteloze status en vraag `replaceCurrentItem`.
1. Het item afspelen.

   * Als het item is geladen maar niet is gebufferd:

      1. Wacht op geïnitialiseerde status.
      1. Bel `prepareToPlay()`.
      1. Wacht op de status PREPARED.
      1. Bel `play()`.
   * Als het item is gebufferd:

      1. Wacht op de gebeurtenis die in de buffer is voorbereid.
      1. Bel `play()`.