---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
seo-title: Kwaliteit van de dienststatistieken
title: Kwaliteit van de dienststatistieken
uuid: c08c1031-616a-4776-92e2-1c405467689b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Kwaliteit van de dienststatistieken {#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

## De playback van QOS, het bufferen, en apparatenstatistieken lezen {#section_9996406E2D814FA382B77E3041CB02BC}

U kunt het afspelen, bufferen en apparaatstatistieken lezen van de `PTQOSProvider` klasse.

De `PTQOSProvider` klasse biedt diverse statistieken, waaronder informatie over buffering, bitsnelheden, framesnelheden, tijdgegevens enzovoort.

Het biedt ook informatie over het apparaat, zoals het model, het besturingssysteem en de apparaat-id van de fabrikant.

>[!TIP]
>
>U kunt de grootte van de afspeelbuffer niet wijzigen, maar u kunt wel de status van de buffergrootte voor foutopsporing of analyse controleren. `PTPlaybackInformation` bevat eigenschappen zoals `playbackBufferFull` en `playbackLikelyToKeepUp`.

1. Instantiëren van een mediaspeler.
1. Maak een `PTQOSProvider` object en koppel dit aan de mediaspeler.

   De `PTQOSProvider` constructor gebruikt een spelercontext zodat deze apparaatspecifieke informatie kan ophalen.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer, zoals hebben `NSTimer`, die periodiek de nieuwe waarden QoS van `PTQOSProvider`. haalt. Bijvoorbeeld:

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
