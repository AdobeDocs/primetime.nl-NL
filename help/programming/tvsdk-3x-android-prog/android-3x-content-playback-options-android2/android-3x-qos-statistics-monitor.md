---
description: De kwaliteit van de dienst (QoS) verstrekt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-description: De kwaliteit van de dienst (QoS) verstrekt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-title: Kwaliteit van de dienststatistieken
title: Kwaliteit van de dienststatistieken
uuid: 3d66ed44-9d4a-4162-962f-e238575ff2dd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Kwaliteit van de dienststatistieken {#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) verstrekt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

TVSDK biedt ook informatie over de volgende gedownloade bronnen:

* Afspeellijst-/manifestbestanden
* Bestandsfragmenten
* Gegevens bijhouden voor bestanden

## Bijhouden op fragmentniveau met behulp van laadgegevens {#section_4439D91E8EDC45588EF1D7BE25697350}

U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van de `LoadInformation` klasse lezen.

1. Implementeer en registreer de gebeurtenislistener `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE`.
1. Roep `event.getLoadInformation()` aan om de relevante gegevens van de `event` parameter te lezen die aan callback wordt overgegaan.

   >[!NOTE]
   >
   >Zie `LoadInformation`3.0 for Android (Java)[ API docs voor meer informatie.](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.0/index.html)

## De playback van QOS, het bufferen, en apparatenstatistieken {#section_D21722600F324E67A9F06234D338B243} lezen

U kunt het afspelen, het bufferen, en apparatenstatistieken van de `QOSProvider` klasse lezen.

De klasse `QOSProvider` verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc. Het biedt ook informatie over het apparaat, zoals de fabrikant, het model, het besturingssysteem, de SDK-versie, de apparaat-id van de fabrikant en schermgrootte/dichtheid.

1. Instantiëren van een mediaspeler.
1. Maak een `QOSProvider`-object en koppel dit aan de mediaspeler.

   De constructor `QOSProvider` neemt de spelercontext zodat deze apparaatspecifieke informatie kan ophalen.

   ```java
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider(getActivity().getApplicationContext()); 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer hebben, die periodiek de nieuwe waarden QoS van `QOSProvider` haalt.

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
