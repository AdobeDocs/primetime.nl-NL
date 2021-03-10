---
description: De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.
title: Direct aan
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# Meteen op {#instant-on}

De term instant op verwijst naar het vooraf laden van een of meer kanalen, zodat een gebruiker die een kanaal selecteert of schakelt kanalen de inhoud direct ziet afspelen. De buffering is al uitgevoerd tegen de tijd dat de gebruiker begint te kijken.

Zonder instant on initialiseert TVSDK de media die moeten worden afgespeeld, maar start de buffering van de stream pas wanneer de toepassing `play` aanroept. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met onmiddellijke ingang kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen.

Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen onmiddellijk gestart wanneer `play` op het nieuwe kanaal wordt aangeroepen.

Hoewel er geen grenzen aan het aantal instanties `MediaPlayer` zijn die TVSDK kan lopen, verbruikt het runnen van meer instanties meer middelen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Zie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md) voor meer informatie over deze instanties.

## Buffering configureren voor direct afspelen {#configure-buffering-for-instant-on-playback}

Met onmiddellijke aan, kunnen de gebruikers kanalen schakelen en het playback begint onmiddellijk zonder wachttijd. Wanneer u onmiddellijk inschakelt, buffert TVSDK een of meer kanalen voordat het afspelen begint.

1. Bevestig dat de bron is geladen en klaar is voor afspelen door te controleren of de status PREPARED is.
1. Roep `prepareBuffer` voor elke `MediaPlayer`-instantie aan voordat u `play` aanroept.

   Dit laat onmiddellijk toe, wat betekent dat TVSDK begint als buffer op te treden zonder eigenlijk het media middel te spelen. TVSDK verzendt de gebeurtenis `BUFFERING_COMPLETED` wanneer de buffer vol is.

   >[!NOTE]
   >
   >`prepareBuffer` en `prepareToPlay` zetten standaard de mediastream in om vanaf het begin af te spelen. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) door aan `prepareToPlay`.

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

1. Wanneer u de gebeurtenis `BUFFERING_COMPLETE` ontvangt, begin het punt te spelen of toon visuele terugkoppelen om erop te wijzen dat de inhoud volledig als buffer voor is.

   Als u `play` roept, zou het playback onmiddellijk moeten beginnen.

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
