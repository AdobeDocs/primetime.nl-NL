---
description: De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.
seo-description: De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.
seo-title: Direct aan
title: Direct aan
uuid: 4cb4d221-170f-46e8-af26-32f259377617
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Direct aan {#instant-on}

De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.

Zonder onmiddellijk aan, initialiseert TVSDK de media om te spelen maar begint niet de stroom in de buffer op te slaan tot de toepassing roept `play`. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met onmiddellijke ingang kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen.

Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen onmiddellijk gestart wanneer `play` de gebruiker het nieuwe kanaal aanroept.

Hoewel er geen grenzen aan het aantal `MediaPlayer` instanties zijn dat TVSDK kan lopen, verbruikt het runnen van meer instanties meer middelen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Zie Een mediabron [laden met MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md)voor meer informatie over deze instanties.

## Buffering configureren voor onmiddellijk afspelen {#configure-buffering-for-instant-on-playback}

Met onmiddellijk aan, kunnen de gebruikers kanalen schakelen en het playback begint onmiddellijk zonder wachttijd. Wanneer u onmiddellijk inschakelt, buffert TVSDK een of meer kanalen voordat het afspelen begint.

1. Bevestig dat de bron is geladen en klaar is voor afspelen door te controleren of de status PREPARED is.
1. Roep `play`voor elke `prepareBuffer` `MediaPlayer` instantie aan voordat u deze aanroept.

   Dit laat onmiddellijk toe, wat betekent dat TVSDK begint als buffer op te treden zonder eigenlijk het media middel te spelen. TVSDK verzendt de `BUFFERING_COMPLETED` gebeurtenis wanneer de buffer vol is.

   >[!NOTE]
   >
   >De mediastream wordt standaard `prepareBuffer` `prepareToPlay` en vanaf het begin afgespeeld. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) door aan `prepareToPlay`.

   ```java
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state,  
                              MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               // By default, prepareToPlay and prepareBuffer buffer and start playing 
               // from the beginning of the stream. To start at another position, 
               // pass it into prepareToPlay. This example starts 5 seconds into the stream. 
               _mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               _mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Wanneer u de `BUFFERING_COMPLETE` gebeurtenis ontvangt, begint het punt te spelen of visuele terugkoppelen om erop te wijzen dat de inhoud volledig als buffer op is gebufferd.

   Als u roept `play`, zou het playback onmiddellijk moeten beginnen.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
