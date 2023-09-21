---
description: Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.
title: Direct aan
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Direct aan {#instant-on}

Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.

Zonder Instant On initialiseert TVSDK de media die moeten worden afgespeeld, maar start de buffering van de stream pas wanneer de toepassing wordt aangeroepen `play`. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met Instant On kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt `play` op het nieuwe kanaal begint onmiddellijk met afspelen.

Hoewel het aantal `MediaPlayer` en `MediaPlayerItemLoader` instanties die door TVSDK kunnen worden uitgevoerd en waarop meer instanties worden uitgevoerd, verbruikt meer bronnen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Voor meer informatie over `MediaPlayerItemLoader`, zie [Een mediabron laden in de mediaspeler](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md).

>[!IMPORTANT]
>
>TVSDK biedt geen ondersteuning voor één `QoSProvider` werken met beide `itemLoader` en `MediaPlayer`. Als de klant Onmiddellijk gebruikt, moet de toepassing twee instanties handhaven QoS en beide instanties voor de informatie beheren.

Voor meer informatie over `MediaPlayerItemLoader`, zie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

## Een instantie QoS Provider toevoegen aan mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Een QoS-provider maken en koppelen aan een `mediaPlayerItemLoader` instance

  ```
  // Create an instance of QoSProvider  
  private QOSProvider _qosProvider = new QOSProvider(this._context);  
  
  // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
  // (before calling load API on mediaPlayerItemLoader instance)  
  _qosProvider.attachMediaPlayerItemLoader(this._loader); 
  ```

  Wanneer het afspelen begint, gebruikt u de `_qosProvider` om te worden `timeToLoad` en `timeToPrepare` QoSdata. De resterende metriek QoS kan worden teruggewonnen door te gebruiken `QoSProvider` aan de `mediaPlayer`.

  Voor meer informatie over `MediaPlayerItemLoader`, zie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

## Buffering configureren voor Instant On {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK biedt methoden en statussen waarmee u Direct On kunt gebruiken met een mediabron.

>[!NOTE]
>
>Adobe raadt u aan `MediaPlayerItemLoader` voor InstantOn. Te gebruiken `MediaPlayerItemLoader`, in plaats van `MediaPlayer`, zie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

1. Controleer of de bron is geladen en of de speler bereid is de resource af te spelen.
1. Vóór het aanroepen `play`, aanroepen `prepareBuffer` voor elke `MediaPlayer` -instantie.

   `prepareBuffer` schakelt Instant On in en TVSDK start de buffering onmiddellijk en verzendt de `BUFFERING_COMPLETED` gebeurtenis wanneer de buffer vol is.

   >[!TIP]
   >
   >Standaard, `prepareBuffer` en `prepareToPlay` Stel de mediastream in om vanaf het begin af te spelen. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) aan `prepareToPlay`.

   ```
   @Override 
   public void onStatusChanged(MediaPlayerStatus status) { 
       switch (status) { 
           case INITIALIZED: 
               // This example starts 5 seconds into the stream. 
               mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. Wanneer u de `BUFFERING_COMPLETE` -gebeurtenis, het afspelen van het item starten of visuele feedback weergeven om aan te geven dat de inhoud volledig is gebufferd.

   >[!NOTE]
   >
   >Als u `play`, moet het afspelen onmiddellijk beginnen.
