---
description: De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.
title: Kwaliteit van de dienststatistieken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---


# Kwaliteit van de dienststatistieken{#quality-of-service-statistics}

De kwaliteit van de dienst (QoS) biedt een gedetailleerde mening in hoe de videomotor presteert. TVSDK biedt gedetailleerde statistieken over het afspelen, bufferen en apparaten.

## De playback van QOS, het bufferen, en apparatenstatistieken {#section_9996406E2D814FA382B77E3041CB02BC} lezen

U kunt het afspelen, het bufferen, en apparatenstatistieken van de `PTQOSProvider` klasse lezen.

De klasse `PTQOSProvider` verstrekt diverse statistieken, met inbegrip van informatie over het als buffer optreden voor, beetjetarieven, kadertarieven, tijdgegevens, etc.

Het biedt ook informatie over het apparaat, zoals het model, het besturingssysteem en de apparaat-id van de fabrikant.

>[!TIP]
>
>U kunt de grootte van de afspeelbuffer niet wijzigen, maar u kunt wel de status van de buffergrootte voor foutopsporing of analyse controleren. `PTPlaybackInformation` bevat eigenschappen zoals  `playbackBufferFull` en  `playbackLikelyToKeepUp`.

1. Instantiëren van een mediaspeler.
1. Maak een `PTQOSProvider`-object en koppel dit aan de mediaspeler.

   De constructor `PTQOSProvider` neemt de spelercontext zodat deze apparaatspecifieke informatie kan ophalen.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Optioneel) Lees de afspeelstatistieken.

   Één oplossing om playbackstatistieken te lezen moet een tijdopnemer, zoals `NSTimer` hebben, die periodiek de nieuwe waarden QoS van `PTQOSProvider` haalt. Bijvoorbeeld:

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

