---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-title: Kwaliteit van de dienststatistieken
title: Kwaliteit van de dienststatistieken
uuid: 5c9d09a9-0e0b-44f2-98ca-2eeb8a830ec6
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Kwaliteit van de dienststatistieken {#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

TVSDK biedt ook informatie over de volgende gedownloade bronnen:

* Afspeellijst-/manifestbestanden
* Bestandsfragmenten
* Gegevens bijhouden voor bestanden

## Bijhouden op fragmentniveau met behulp van laadgegevens {#track-at-the-fragment-level-using-load-information}

U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van de klasse lezen LoadInformation.

1. Implementeer de callback-gebeurtenislistener `onLoadInformationAvailable`.

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. Registreer de gebeurtenislistener, die door TVSDK wordt aangeroepen telkens wanneer een fragment is gedownload.

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. Lees de gegevens van belang van `LoadInformation` die tot callback wordt overgegaan.

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> Eigenschap </th> 
      <th colname="col1" class="entry"> Type </th> 
      <th colname="col2" class="entry"> Beschrijving </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration  </span> </td> 
      <td colname="col1"> <p>Getal </p> </td> 
      <td colname="col2"> <p>De duur van de download in milliseconden. </p> <p>TVSDK maakt geen onderscheid tussen de tijd dat de client verbinding heeft gemaakt met de server en de tijd die nodig was om het volledige fragment te downloaden. Bijvoorbeeld, als een 10 MB segment 8 seconden aan download vergt, verstrekt TVSDK die informatie, maar vertelt u niet dat het 4 seconden tot de eerste byte en nog eens 4 seconden kostte om het volledige fragment te downloaden. </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration  </span> </td> 
      <td colname="col1"> <p>Getal </p> </td> 
      <td colname="col2"> De mediaduur van de gedownloade fragmenten in milliseconden. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> size  </span> </td> 
      <td colname="col1"> <p>Getal </p> </td> 
      <td colname="col2"> De grootte van de gedownloade bron in bytes. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex  </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> de index van het overeenkomstige spoor, indien bekend; anders, 0. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName  </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> de naam van de overeenkomstige spoorbaan, indien bekend; anders, null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType  </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> het type van het overeenkomstige spoor, indien bekend; anders, null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type  </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> Wat heeft TVSDK gedownload. Een van de volgende opties: 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST - Een afspeellijst/manifest </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT - Een fragment </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK - Een fragment dat is gekoppeld aan een specifieke track </li> 
      </ul> Soms is het mogelijk dat het type van de bron niet kan worden gedetecteerd. Als dit gebeurt, wordt FILE geretourneerd. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url  </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> De URL die naar de gedownloade bron wijst. </td> 
   </tr> 
   </tbody> 
   </table>

## De playback van QOS, het bufferen, en apparatenstatistieken {#read-qos-playback-buffering-and-device-statistics} lezen

U kunt playback, het als buffer optreden voor, en apparatenstatistieken van de klasse lezen QOSProvider.

De klasse `QOSProvider` verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc.

Het biedt ook informatie over het apparaat, zoals de fabrikant, het model, het besturingssysteem, de SDK-versie en schermgrootte/dichtheid.

1. Instantiëren van een mediaspeler.
1. Maak een `QOSProvider`-object en koppel dit aan de mediaspeler.

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer hebben, die periodiek de nieuwe waarden QoS van `QOSProvider` haalt. Bijvoorbeeld:

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
