---
description: Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.
seo-description: Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.
seo-title: Een mediabron laden met MediaPlayerItemLoader
title: Een mediabron laden met MediaPlayerItemLoader
uuid: 43ca2470-1fd2-4f66-94fe-a12ed17b52d7
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Een mediabron laden met MediaPlayerItemLoader {#load-a-media-resource-using-mediaplayeritemloader}

Het gebruik van MediaPlayerItemLoader helpt u informatie over een mediastream te verkrijgen zonder een instantie MediaPlayer te instantiëren. Dit is vooral handig bij het vooraf bufferen van streams, zodat het afspelen zonder vertraging kan beginnen.

De `MediaPlayerItemLoader` klasse helpt u een media middel voor huidige `MediaPlayerItem` ruilen zonder een mening aan een `MediaPlayer` instantie vast te maken, die video het decoderen hardwaremiddelen zou toewijzen. Extra stappen zijn nodig voor met DRM beveiligde inhoud, maar deze handleiding bevat geen beschrijving van de stappen.

>[!IMPORTANT]
>
>TVSDK ondersteunt geen enkele `QoSProvider` om met zowel `itemLoader` als `MediaPlayer` te werken. Als uw toepassing Instant On gebruikt, moet de toepassing twee `QoS` instanties handhaven en beide instanties voor de informatie beheren. Zie [instant-on](../../content-playback-options/buffering-configuration/c-psdk-android-2.7-instant-on.md) voor meer informatie.

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
   >Maak een afzonderlijk exemplaar van `MediaPlayerItemLoader` voor elke bron. Gebruik geen `MediaPlayerItemLoader`-instantie om meerdere bronnen te laden.

1. Implementeer de klasse `ItemLoaderListener` om meldingen van de instantie `MediaPlayerItemLoader` te ontvangen.

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

   Voer in de callback `onLoadComplete()` een van de volgende handelingen uit:

   * Zorg ervoor dat alles wat buffering kan beïnvloeden, bijvoorbeeld door WebVTT of audiotracks te selecteren, volledig is en `prepareBuffer()` aanroep om direct voordeel te halen uit de functie.
   * Koppel het item aan de instantie `MediaPlayer` met `replaceCurrentItem()`.

   Als u `prepareBuffer()` roept, ontvangt u de gebeurtenis BUFFER_PREPARED in uw `onBufferPrepared` manager wanneer de voorbereiding wordt gebeëindigd.

1. Roep `load` op de `MediaPlayerItemLoader` instantie en geef de te laden bron, en optioneel de inhoud-id, en een `MediaPlayerItemConfig`-instantie door.

   ```java
   loader = createLoader(); 
   MediaResource res = new MediaResource(mVideoUrl, MediaResource.Type.HLS, metadata); 
   loader.load(res, 233, getConfig());
   ```

1. Als u vanaf een ander punt dan het begin van de stream wilt bufferen, roept u `prepareBuffer()` aan met de positie (in milliseconden) waarop het bufferen moet worden gestart.
1. Gebruik de methoden `replaceCurrentItem()` en `play()` van `MediaPlayer` om vanaf dat punt af te spelen.
1. Wacht op nutteloze status en vraag `replaceCurrentItem`.
1. Het item afspelen.

   * Als het item is geladen maar niet is gebufferd:

      1. Wacht op geïnitialiseerde status.
      1. Roep `prepareToPlay()`.
      1. Wacht op de status PREPARED.
      1. Roep `play()`.
   * Als het item is gebufferd:

      1. Wacht op de gebeurtenis die in de buffer is voorbereid.
      1. Roep `play()`.