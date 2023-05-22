---
description: In Browser TVSDK, kunt u aan een specifieke positie (tijd) in een stroom zoeken. Een stream kan een afspeellijst met schuifvensters of VOD-inhoud (video on demand) zijn.
title: Handgreep zoeken bij gebruik van de zoekbalk
exl-id: 4c09b218-917a-4318-82b0-c221d450a2c1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Handgreep zoeken bij gebruik van de zoekbalk{#handle-seek-when-using-the-seek-bar}

In Browser TVSDK, kunt u aan een specifieke positie (tijd) in een stroom zoeken. Een stream kan een afspeellijst met schuifvensters of VOD-inhoud (video on demand) zijn.

>[!IMPORTANT]
>
>Zoeken in een live stream is alleen toegestaan voor DVR.

1. Wacht tot Browser TVSDK geldig is voor zoeken.

   Geldige statussen worden BEREID, VOLTOOID, GEPAUZEERD en AFGESPEELD. Als u in een geldige status werkt, weet u zeker dat de mediabrondel is geladen. Als de speler zich niet in een geldige, doorzoekbare status bevindt, wordt bij een poging de volgende methoden aan te roepen een `IllegalStateException`.

   U kunt bijvoorbeeld wachten tot Browser TVSDK wordt geactiveerd  `AdobePSDK.MediaPlayerStatusChangeEvent`  met een `event.status` van `AdobePSDK.MediaPlayerStatus.PREPARED`.

1. Geef de gewenste positie in de zoekopdracht door aan de `MediaPlayer.seek` als een parameter in milliseconden.

   Hierdoor wordt de afspeelkop naar een andere positie in de stream verplaatst.

   >[!TIP]
   >
   >De gevraagde positie komt mogelijk niet overeen met de werkelijk berekende positie.

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Wacht tot Browser TVSDK de  `AdobePSDK.PSDKEventType.SEEK_END`  gebeurtenis, die de aangepaste positie in de gebeurtenis terugkeert `actualPosition` kenmerk:

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   Dit is belangrijk omdat de werkelijke startpositie na de zoekactie anders kan zijn dan de gewenste positie. Een aantal van de volgende regels kan van toepassing zijn:

   * Het afspeelgedrag wordt beïnvloed als een zoekopdracht of een andere verplaatsing in het midden van een advertentiesleutel eindigt of als een zoekopdracht of andere verplaatsing wordt overgeslagen en afgebroken.
   * U kunt alleen zoeken in de doorzoekbare duur van het element. Voor VOD, dat van 0 door de duur van het activa is.

1. Voor de zoekbalk die in het bovenstaande voorbeeld is gemaakt, luistert u naar `setPositionChangeListener()` om te zien wanneer de gebruiker scrubt:

   ```js
   seekBar.setPositionChangeListener(function (pos) { 
                   var range = player.seekableRange; 
                   if (range) { 
                       var duration = range.duration; 
                       var time = duration * pos; // seek bar range is [0,1] 
                       player.seek(time); 
   
                       console.log("seek to " + time + " / " + duration); 
                   } 
   
               }); 
   ```

1. Stel gebeurtenislistener-callbacks in voor wijzigingen in de zoekactiviteit van de gebruiker.

       De zoekbewerking is asynchroon, zodat Browser TVSDK de volgende gebeurtenissen verstuurt met betrekking tot zoeken:
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` om aan te geven dat de zoekactie wordt gestart.
   * `AdobePSDK.PSDKEventType.SEEK_END` om aan te geven dat het zoeken is geslaagd.
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` om aan te geven dat de mediaspeler de door de gebruiker opgegeven zoekpositie heeft aangepast.
