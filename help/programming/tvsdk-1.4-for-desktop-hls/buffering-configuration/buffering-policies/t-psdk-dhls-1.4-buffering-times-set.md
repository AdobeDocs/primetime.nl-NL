---
description: De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.
title: Buffertijden instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Buffertijden instellen{#set-buffering-times}

De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

1. Stel de `BufferControlParameters` object, dat de initiële parameters voor buffertijd en afspeelbuffertijd inkapselt:

       Deze klasse biedt de volgende fabrieksmethoden:
   
   * De eerste buffertijd instellen op gelijk aan de buffertijd van het afspelen:

     ```
     createSimple(bufferTime:uint):BufferControlParameters
     ```

   * U stelt als volgt de buffertijden voor initialen en afspelen in:

     ```
     createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
     ```

     Deze methoden genereren een `IllegalArgumentException` als de parameters niet geldig zijn, bijvoorbeeld wanneer:

   * De aanvankelijke buffertijd is minder dan nul.
   * De aanvankelijke buffertijd is groter dan de buffertijd.

1. Gebruik deze optie om de bufferparameterwaarden in te stellen `MediaPlayer` methode:

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. Als u de huidige bufferparameterwaarden wilt ophalen, gebruikt u deze `MediaPlayer` methode:

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Stel bijvoorbeeld de eerste buffer in op 2 seconden en de buffertijd voor het afspelen op 30 seconden:

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

De `psdkdemo` demonstreert deze functie; gebruik de instellingen van de toepassing om de bufferwaarden in te stellen.
