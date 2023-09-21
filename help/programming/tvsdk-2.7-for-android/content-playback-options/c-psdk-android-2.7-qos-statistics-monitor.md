---
description: De kwaliteit van de dienst (QoS) verstrekt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
title: Kwaliteit van de dienststatistieken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Kwaliteit van de dienststatistieken {#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) verstrekt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

TVSDK biedt ook informatie over de volgende gedownloade bronnen:

* Afspeellijst-/manifestbestanden
* Bestandsfragmenten
* Gegevens bijhouden voor bestanden

## Bijhouden op fragmentniveau met behulp van laadgegevens {#section_4439D91E8EDC45588EF1D7BE25697350}

U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van `LoadInformation` klasse.

1. Implementeren en registreren van de `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` gebeurtenislistener.
1. Bellen `event.getLoadInformation()` de relevante gegevens van de `event` parameter die aan callback wordt overgegaan.

   >[!NOTE]
   >
   >Voor meer informatie `LoadInformation`, zie [2.7 voor Android (Java)](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html) API-documenten.

## De playback van QOS, het als buffer optreden voor, en apparatenstatistieken lezen {#section_D21722600F324E67A9F06234D338B243}

U kunt de statistische gegevens over het afspelen, bufferen en apparaat lezen vanuit de `QOSProvider` klasse.

De `QOSProvider` klasse verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc. Het biedt ook informatie over het apparaat, zoals de fabrikant, het model, het besturingssysteem, de SDK-versie, de apparaat-id van de fabrikant en schermgrootte/dichtheid.

1. Een mediaspeler instantiëren.
1. Een `QOSProvider` en aan de mediaspeler koppelen.

   De `QOSProvider` constructor gebruikt een spelercontext zodat deze apparaatspecifieke informatie kan ophalen.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer hebben, die periodiek de nieuwe waarden QoS van de `QOSProvider`.

   Bijvoorbeeld:

   ```java
   _playbackClock = new Clock(PLAYBACK_CLOCK, 1000); // every 1 second 
   _playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           getActivity().runOnUiThread(new Runnable() { 
               @Override 
               public void run() { 
                   PlaybackInformation playbackInformation =  
                     _mediaQosProvider.getPlaybackInformation();  
                   setQosItem("Frame rate", (int) playbackInformation.getFrameRate());  
                   setQosItem("Dropped frames", (int) playbackInformation.getDroppedFrameCount()); 
                   setQosItem("Bitrate", (int) playbackInformation.getBitrate()); 
                   setQosItem("Buffering time", (int) playbackInformation.getBufferingTime());  
                   setQosItem("Buffer length", (int) playbackInformation.getBufferLength());  
                   setQosItem("Buffer time", (int) playbackInformation.getBufferTime());  
                   setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount());  
                   setQosItem("Time to load", (int) playbackInformation.getTimeToLoad());  
                   setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); 
                   setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); 
                   setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());   
                   playbackInformation.getPerceivedBandwidth()); 
               } 
           }); 
       }; 
   }; 
   ```

1. (Optioneel) Lees de apparaatspecifieke informatie.

   ```java
   // Show device information 
   DeviceInformation deviceInfo = new QOSProvider(parent.getApplicationContext()). 
                                  getDeviceInformation(); 
   tv = (TextView) view.findViewById(R.id.aboutDeviceModel); 
   tv.setText(parent.getString(R.string.aboutDeviceModel) + " " +  
     deviceInfo.getManufacturer() + " - " + deviceInfo.getModel()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceSoftware); 
   tv.setText(parent.getString(R.string.aboutDeviceSoftware) + " " +  
     deviceInfo.getOS() + ", SDK: " + deviceInfo.getSDK()); 
   
   tv = (TextView) view.findViewById(R.id.aboutDeviceResolutin); 
   String orientation = parent.getResources().getConfiguration().orientation ==  
     Configuration.ORIENTATION_LANDSCAPE ? "landscape" : "portrait"; 
   tv.setText(parent.getString(R.string.aboutDeviceResolution) + " " +  
     deviceInfo.getWidthPixels() + "x" + deviceInfo.getHeightPixels() +  
     " (" + orientation + ")"); 
   ```
