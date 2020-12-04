---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. Browser TVSDK verstrekt gedetailleerde statistieken over playback, het als buffer optreden, en apparaten.
seo-description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. Browser TVSDK verstrekt gedetailleerde statistieken over playback, het als buffer optreden, en apparaten.
seo-title: Kwaliteit van de dienststatistieken
title: Kwaliteit van de dienststatistieken
uuid: e4bb2617-d8a7-4da7-b669-d6ffab2864bb
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---


# Kwaliteit van de dienststatistieken{#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. Browser TVSDK verstrekt gedetailleerde statistieken over playback, het als buffer optreden, en apparaten.

## De playback van QOS, het bufferen, en apparatenstatistieken {#read-qos-playback-buffering-and-device-statistics} lezen

U kunt playback, het als buffer optreden voor, en apparatenstatistieken van de klasse lezen QOSProvider.

De klasse `QOSProvider` verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc.

1. Instantiëren van een mediaspeler.
1. Maak een `QOSProvider`-object en koppel dit aan de mediaspeler.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer hebben, die periodiek de nieuwe waarden QoS van `QOSProvider` haalt. Bijvoorbeeld:

   ```js
   var qosTimer = (function () { 
       var ref = null, 
       qosChangeInterval = 500, // in milliseconds 
   
       startTimer = function () { 
           var playbackInformation = qosProvider.playbackInformation; 
        console.log("Frame rate", playbackInformation.frameRate); 
           console.log ("Dropped frames", playbackInformation.droppedFrameCount); 
           console.log ("Bitrate", playbackInformation.bitrate); 
           console.log ("Buffering time", playbackInformation.bufferingTime); 
           console.log ("Buffer length", playbackInformation.bufferLength); 
           console.log ("Buffer time", playbackInformation.bufferTime); 
           console.log ("Empty buffer count", playbackInformation.emptyBufferCount); 
           console.log ("Time to load", playbackInformation.timeToLoad); 
           console.log ("Time to start", playbackInformation.timeToStart); 
           ref = window.setTimeout(startTimer, qosChangeInterval); 
       }; 
   
       return { 
           start: function () { 
               if (ref !== null) { 
                   // don't start another timeout if one already exists. 
                   return; 
               } 
               startTimer(); 
           }, 
   
           stop: function () { 
               window.clearTimeout(ref); 
               ref = null; 
           } 
       };  
   })() 
   
   qosTimer.start(); 
   ```

1. (Optioneel) Lees de apparaatspecifieke informatie.

   ```js
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider().deviceInformation; 
   console.log("OS: "+ deviceInfo.getOS()); 
   console.log("Width: "+ deviceInfo.getWidthPixels() +  
               "Height: "+ deviceInfo.getHeightPixels() );
   ```
