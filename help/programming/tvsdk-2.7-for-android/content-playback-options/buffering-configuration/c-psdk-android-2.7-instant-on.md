---
description: Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.
title: Direct aan
exl-id: a9c0b9d0-ef2b-4113-bd08-e2b2792b04fb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Direct aan {#instant-on}

Als u de functie Onmiddellijk inschakelen inschakelt, wordt een of meer kanalen vooraf geladen. Wanneer gebruikers een kanaal selecteren of schakelen tussen kanalen, wordt de inhoud direct afgespeeld. De buffering is voltooid tegen de tijd dat de gebruiker begint te kijken.

Zonder Instant On initialiseert TVSDK de media die moeten worden afgespeeld, maar start de buffering van de stream pas wanneer de toepassing wordt aangeroepen `play`. De gebruiker ziet geen inhoud totdat de buffering is voltooid. Met Instant On kunt u meerdere media Player-instanties (of media-player-itemloader) starten en TVSDK begint de streams direct te bufferen. Wanneer een gebruiker het kanaal wijzigt en de stream correct is gebufferd, wordt `play` op het nieuwe kanaal begint onmiddellijk met afspelen.

Hoewel het aantal `MediaPlayer` en `MediaPlayerItemLoader` instanties die door TVSDK kunnen worden uitgevoerd en waarop meer instanties worden uitgevoerd, verbruikt meer bronnen. De prestaties van de toepassing kunnen worden beïnvloed door het aantal exemplaren dat wordt uitgevoerd. Meer informatie over `MediaPlayerItemLoader`, zie [Een mediabron laden in de mediaspeler](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load.md).

>[!IMPORTANT]
>
>TVSDK biedt geen ondersteuning voor één `QoSProvider` werken met beide `itemLoader` en `MediaPlayer`. Als de klant Onmiddellijk gebruikt, moet de toepassing twee instanties handhaven QoS en beide instanties voor de informatie beheren.

Meer informatie over `MediaPlayerItemLoader`, zie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

## Een instantie van een QoS-provider toevoegen aan mediaPlayerItemLoader {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* Een QoS-provider maken en koppelen aan een `mediaPlayerItemLoader` instance

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   Wanneer het afspelen begint, gebruikt u de `_qosProvider` om te worden `timeToLoad` en `timeToPrepare` QoSdata. De resterende metriek QoS kan worden teruggewonnen door te gebruiken `QoSProvider` aan de `mediaPlayer`.

   Meer informatie over `MediaPlayerItemLoader`, zie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md#use-mediaplayeritemloader).

## Buffering configureren voor Instant On {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK biedt methoden en statussen waarmee u Direct On kunt gebruiken met een mediabron.

>[!NOTE]
>
>Adobe raadt u aan `MediaPlayerItemLoader` voor InstantOn. Te gebruiken `MediaPlayerItemLoader`, in plaats van `MediaPlayer`, zie media-middel-lading-using-mediaplayeritemloader.

1. Controleer of de bron is geladen en of de speler bereid is de resource af te spelen.
1. Vóór het aanroepen `play`, aanroepen `prepareBuffer` voor elke `MediaPlayer` -instantie.

   >[!NOTE]
   >
   >`prepareBuffer` schakelt Instant On in en TVSDK start de buffering onmiddellijk en verzendt de `BUFFERING_COMPLETED` gebeurtenis wanneer de buffer vol is.

   >[!TIP]
   >
   >Standaard, `prepareBuffer` en `prepareToPlay` Stel de mediastream in om vanaf het begin af te spelen. Als u op een andere positie wilt beginnen, geeft u de positie (in milliseconden) door aan `prepareToPlay`.

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
