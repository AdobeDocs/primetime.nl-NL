---
description: De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.
title: Direct aan
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Direct aan {#instant-on}

De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.

TVSDK initialiseert zonder onmiddellijk de media die moeten worden afgespeeld, maar start de buffering van de stream pas wanneer de toepassing wordt aangeroepen `play`. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met onmiddellijke ingang kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen.

Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt `play` op het nieuwe kanaal begint onmiddellijk met afspelen.

Hoewel het aantal `MediaPlayer` instanties die door TVSDK kunnen worden uitgevoerd en waarop meer instanties worden uitgevoerd, verbruikt meer bronnen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Zie voor meer informatie over deze instanties [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## Buffering configureren voor onmiddellijk afspelen {#configure-buffering-for-instant-on-playback}

Met onmiddellijk aan, kunnen de gebruikers kanalen schakelen en het playback begint onmiddellijk zonder wachttijd. Wanneer u onmiddellijk inschakelt, buffert TVSDK een of meer kanalen voordat het afspelen begint.

1. Bevestig dat de bron is geladen en klaar is voor afspelen door te controleren of de status PREPARED is.
1. Vóór het aanroepen `play`, aanroepen `prepareBuffer` voor elke `MediaPlayer` -instantie.

   Dit laat onmiddellijk toe, wat betekent dat TVSDK begint als buffer op te treden zonder eigenlijk het media middel te spelen. TVSDK verzendt de `BUFFERING_COMPLETED` gebeurtenis wanneer de buffer vol is.

   >[!NOTE]
   >
   >Standaard, `prepareBuffer` en `prepareToPlay` Stel de mediastream in om vanaf het begin af te spelen. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) door aan `prepareToPlay`.

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

1. Wanneer u de `BUFFERING_COMPLETE` -gebeurtenis, het afspelen van het item starten of visuele feedback weergeven om aan te geven dat de inhoud volledig is gebufferd.

   Als u `play`, moet het afspelen onmiddellijk beginnen.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
