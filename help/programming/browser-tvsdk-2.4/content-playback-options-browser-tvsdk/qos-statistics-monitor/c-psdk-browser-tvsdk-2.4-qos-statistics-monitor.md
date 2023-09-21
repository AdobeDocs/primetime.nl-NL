---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. Browser TVSDK verstrekt gedetailleerde statistieken over playback, het als buffer optreden, en apparaten.
title: Kwaliteit van de dienststatistieken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Kwaliteit van de dienststatistieken{#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. Browser TVSDK verstrekt gedetailleerde statistieken over playback, het als buffer optreden, en apparaten.

## De playback van QOS, het als buffer optreden voor, en apparatenstatistieken lezen {#read-qos-playback-buffering-and-device-statistics}

U kunt playback, het als buffer optreden voor, en apparatenstatistieken van de klasse lezen QOSProvider.

De `QOSProvider` klasse verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc.

1. Een mediaspeler instantiëren.
1. Een `QOSProvider` en aan de mediaspeler koppelen.

   ```js
   // Create Media Player.qosProvider =  
         new AdobePSDK.QOSProvider(); 
   qosProvider.attachMediaPlayer(player);
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer hebben, die periodiek de nieuwe waarden QoS van de `QOSProvider`. Bijvoorbeeld:

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
