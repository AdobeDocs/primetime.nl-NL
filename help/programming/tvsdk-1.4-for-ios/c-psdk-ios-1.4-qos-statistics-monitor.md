---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
title: Kwaliteit van de dienststatistieken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Kwaliteit van de dienststatistieken{#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

## De playback van QOS, het als buffer optreden voor, en apparatenstatistieken lezen {#section_9996406E2D814FA382B77E3041CB02BC}

U kunt de statistische gegevens over het afspelen, bufferen en apparaat lezen vanuit de `PTQOSProvider` klasse.

De `PTQOSProvider` klasse verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc.

Het biedt ook informatie over het apparaat, zoals het model, het besturingssysteem en de apparaat-id van de fabrikant.

>[!TIP]
>
>U kunt de grootte van de afspeelbuffer niet wijzigen, maar u kunt wel de status van de buffergrootte voor foutopsporing of analyse controleren. `PTPlaybackInformation` bevat eigenschappen zoals `playbackBufferFull` en `playbackLikelyToKeepUp`.

1. Een mediaspeler instantiëren.
1. Een `PTQOSProvider` en aan de mediaspeler koppelen.

   De `PTQOSProvider` constructor gebruikt een spelercontext zodat deze apparaatspecifieke informatie kan ophalen.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer, zoals hebben `NSTimer`, die periodiek de nieuwe waarden QoS van `PTQOSProvider`. Bijvoorbeeld:

   ```
   - (void)printPlaybackInfoLog { 
       PTPlaybackInformation *playbackInfo = qosProvider.playbackInformation;  
       if (playbackInfo) { 
           // For example: 
           NSString *infoLog = [NSString stringWithFormat:@"observedBitrate :  
                                  %f\n",playbackInfo.observedBitrate]; 
           [consoleView logMessage:@"====%@\n\n",infoLog]; 
       } 
   }
   ```

1. (Optioneel) Lees de apparaatspecifieke informatie.

   ```
    PTDeviceInformation *devInfo = qosProvider.deviceInformation; 
   if (devInfo) { 
       [consoleView logMessage:@"=== qosDeviceInfo:==\n os =%@\n model =  
          %@\n id =%@\n\n", devInfo.os, devInfo.model, devInfo.id]; 
   } 
   [NSTimer scheduledTimerWithTimeInterval:2.0 target:self  
      selector:@selector(printPlaybackInfoLog) userInfo:nil repeats:YES];
   ```
