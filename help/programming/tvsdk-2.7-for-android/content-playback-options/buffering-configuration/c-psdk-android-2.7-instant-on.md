---
description: Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.
seo-description: Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.
seo-title: Direct aan
title: Direct aan
uuid: 7e14b779-2a36-4ff4-a365-9ac49a836ff3
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Direct aan {#instant-on}

Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.

Zonder Instant On initialiseert TVSDK de media die moeten worden afgespeeld, maar start de buffering van de stream pas wanneer de toepassing wordt aangeroepen `play`. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met Instant On kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen onmiddellijk gestart wanneer `play` de gebruiker het nieuwe kanaal aanroept.

Hoewel er geen beperkingen zijn aan het aantal `MediaPlayer` en de `MediaPlayerItemLoader` instanties dat TVSDK kan lopen, verbruikt het runnen van meer instanties meer middelen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Zie Een mediabron in de mediaspeler `MediaPlayerItemLoader`[](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md)laden voor meer informatie over Media.

>[!IMPORTANT]
>
>TVSDK biedt geen ondersteuning voor één functie `QoSProvider` voor zowel `itemLoader` als `MediaPlayer`. Als de klant Onmiddellijk gebruikt, moet de toepassing twee instanties handhaven QoS en beide instanties voor de informatie beheren.

Voor meer informatie over `MediaPlayerItemLoader`, zie [Laad een media middel gebruikend MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

## Een instantie van een QoS-provider toevoegen aan mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Een QoS-provider maken en aan een `mediaPlayerItemLoader` instantie koppelen

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   Wanneer het afspelen is gestart, gebruikt u de code `_qosProvider` om QoSdata `timeToLoad` en `timeToPrepare` QoSdata op te halen. De resterende metriek QoS kan worden teruggewonnen door het `QoSProvider` in bijlage aan `mediaPlayer`. te gebruiken.

   Voor meer informatie over `MediaPlayerItemLoader`, zie [Laad een media middel gebruikend MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md#use-mediaplayeritemloader).

## Buffering configureren voor Instant On {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK biedt methoden en statussen waarmee u Direct On kunt gebruiken met een mediabron.

>[!NOTE]
>
>Adobe raadt u aan `MediaPlayerItemLoader` om InstantOn te gebruiken. Zie media-resource-load-using-mediaplayeritemloader voor gebruik `MediaPlayerItemLoader`in plaats `MediaPlayer`van deze te gebruiken.

1. Controleer of de bron is geladen en of de speler bereid is de resource af te spelen.
1. Roep `play`voor elke `prepareBuffer` `MediaPlayer` instantie aan voordat u deze aanroept.

   >[!NOTE]
   >
   >`prepareBuffer` schakelt Instant On in en TVSDK start de buffering onmiddellijk en verzendt de `BUFFERING_COMPLETED` gebeurtenis wanneer de buffer vol is.

   >[!TIP]
   >
   >De mediastream wordt standaard `prepareBuffer` `prepareToPlay` en vanaf het begin afgespeeld. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) door aan `prepareToPlay`.

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

1. Wanneer u de `BUFFERING_COMPLETE` gebeurtenis ontvangt, begint het punt te spelen of visuele terugkoppelen om erop te wijzen dat de inhoud volledig als buffer op is gebufferd.

   >[!NOTE]
   >
   >Als u roept `play`, zou het playback onmiddellijk moeten beginnen.

