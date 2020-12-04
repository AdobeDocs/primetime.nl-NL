---
description: Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.
seo-description: Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.
seo-title: Direct aan
title: Direct aan
uuid: 7e14b779-2a36-4ff4-a365-9ac49a836ff3
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# Direct aan {#instant-on}

Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.

Zonder Instant On initialiseert TVSDK de media die moeten worden afgespeeld, maar start de buffering van de stream pas wanneer de toepassing `play` aanroept. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met Instant On kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt het afspelen onmiddellijk gestart wanneer `play` op het nieuwe kanaal wordt aangeroepen.

Hoewel er geen grenzen aan het aantal instanties `MediaPlayer` en `MediaPlayerItemLoader` zijn die TVSDK kan lopen, verbruikt het runnen van meer instanties meer middelen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Voor meer informatie over `MediaPlayerItemLoader`, zie [Laad een media middel in de media speler](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

>[!IMPORTANT]
>
>TVSDK ondersteunt geen enkele `QoSProvider` om met zowel `itemLoader` als `MediaPlayer` te werken. Als de klant Onmiddellijk gebruikt, moet de toepassing twee instanties handhaven QoS en beide instanties voor de informatie beheren.

Voor meer informatie over `MediaPlayerItemLoader`, zie [Laad een media middel gebruikend MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

## Een instantie QoS Provider toevoegen aan mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Een QoS-provider maken en koppelen aan een `mediaPlayerItemLoader`-instantie

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   Wanneer het afspelen is gestart, gebruikt u `_qosProvider` om `timeToLoad` en `timeToPrepare` QoSdata te krijgen. De resterende QoS metriek kan worden teruggewonnen door `QoSProvider` te gebruiken in bijlage aan `mediaPlayer`.

   Voor meer informatie over `MediaPlayerItemLoader`, zie [Laad een media middel gebruikend MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md#use-mediaplayeritemloader).

## Buffering configureren voor instant op {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK biedt methoden en statussen waarmee u Direct On kunt gebruiken met een mediabron.

>[!NOTE]
>
>Adobe raadt aan `MediaPlayerItemLoader` voor InstantOn te gebruiken. Zie media-resource-load-using-mediaplayeritemloader voor informatie over het gebruik van `MediaPlayerItemLoader` in plaats van `MediaPlayer`.

1. Controleer of de bron is geladen en of de speler bereid is de resource af te spelen.
1. Roep `prepareBuffer` voor elke `MediaPlayer`-instantie aan voordat u `play` aanroept.

   >[!NOTE]
   >
   >`prepareBuffer` schakelt Instant On in en TVSDK start de buffering onmiddellijk en verzendt de  `BUFFERING_COMPLETED` gebeurtenis wanneer de buffer vol is.

   >[!TIP]
   >
   >`prepareBuffer` en `prepareToPlay` zetten standaard de mediastream in om vanaf het begin af te spelen. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) door aan `prepareToPlay`.

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

1. Wanneer u de gebeurtenis `BUFFERING_COMPLETE` ontvangt, begin het punt te spelen of toon visuele terugkoppelen om erop te wijzen dat de inhoud volledig als buffer voor is.

   >[!NOTE]
   >
   >Als u `play` roept, zou het playback onmiddellijk moeten beginnen.

