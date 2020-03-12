---
description: U kunt playback, het als buffer optreden voor, en apparatenstatistieken van de klasse lezen QOSProvider.
seo-description: U kunt playback, het als buffer optreden voor, en apparatenstatistieken van de klasse lezen QOSProvider.
seo-title: De playback van QOS, het bufferen, en apparatenstatistieken lezen
title: De playback van QOS, het bufferen, en apparatenstatistieken lezen
uuid: 5ee631fc-cd6f-4f35-8621-2ffdc51a57c7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# De playback van QOS, het bufferen, en apparatenstatistieken lezen{#read-qos-playback-buffering-and-device-statistics}

U kunt playback, het als buffer optreden voor, en apparatenstatistieken van de klasse lezen QOSProvider.

De `QOSProvider` klasse biedt diverse statistieken, waaronder informatie over buffering, bitsnelheden, framesnelheden, tijdgegevens enzovoort.

Het biedt ook informatie over het apparaat, zoals de fabrikant, het model, het besturingssysteem, de SDK-versie en schermgrootte/dichtheid.

1. Instantiëren van een mediaspeler.
1. Maak een `QOSProvider` object en koppel dit aan de mediaspeler.

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen is een tijdopnemer te hebben, die periodiek de nieuwe waarden QoS van `QOSProvider`. haalt Bijvoorbeeld:

   ```
   var qosTimer:Timer = new Timer(1000); // every 1 second  
   qosTimer.addEventListener(TimerEvent.Timer, onQoSTimer);  
   qosTimer.start(); 
   private function onQoSTimer(event:TimerEvent):void { 
       var playbackInformation:PlaybackInformation = _mediaQosProvider.getPlaybackInformation(); 
       qosInfo["Frame rate"] = playbackInformation.frameRate.toFixed();  
       qosInfo["Dropped frames"] = playbackInformation.droppedFrameCount.toFixed(); 
       qosInfo["Bitrate"] = playbackInformation.bitrate.toFixed(); 
       qosInfo["Bandwidth"] = playbackInformation.perceivedBandwidth; 
       qosInfo["Buffering time"] = playbackInformation.bufferingTime.toFixed(); 
       qosInfo["Buffer length"] = playbackInformation.bufferLength.toFixed();  
       qosInfo["Buffer time"] = playbackInformation.bufferTime.toFixed(); 
       qosInfo["Empty buffer count"] = playbackInformation.emptyBufferCount.toFixed();  
       qosInfo["Time to load"] = playbackInformation.timeToLoad.toFixed();  
       qosInfo["Time to start"] = playbackInformation.timeToStart.toFixed(); 
       qosView.update(qosInfo); 
   }
   ```

1. (Optioneel) Lees de apparaatspecifieke informatie.

   ```
   // Show device information 
   var deviceInfo:DeviceInformation = new QOSProvider.deviceInformation; 
   qosInfo["deviceModel"] = deviceInfo.manufacturer +"-" + deviceInfo.model; 
   qosInfo["os"] = deviceInfo.os;  
   qosInfo["runtime"] = deviceInfo.runtimeVersion;  
   qosInfo["widthPixels"] = deviceInfo.widthPixels;  
   qosInfo["heightPixels"] = deviceInfo.heightPixels; 
   qosView.update(qosInfo); 
   ```

