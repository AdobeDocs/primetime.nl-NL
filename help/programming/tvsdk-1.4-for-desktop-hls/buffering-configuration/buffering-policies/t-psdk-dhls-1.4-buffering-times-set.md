---
description: De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.
seo-description: De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.
seo-title: Buffertijden instellen
title: Buffertijden instellen
uuid: 25142b01-5381-49c9-b89a-24c858faaf13
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Buffertijden instellen{#set-buffering-times}

De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

1. Stel het `BufferControlParameters` object in, dat de initiële parameters voor buffertijd en afspeelbuffertijd inkapselt:

       Deze klasse biedt de volgende fabrieksmethoden:
   
   * De eerste buffertijd instellen op gelijk aan de buffertijd van het afspelen:

      ```
      createSimple(bufferTime:uint):BufferControlParameters
      ```

   * U stelt als volgt de buffertijden voor initialen en afspelen in:

      ```
      createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
      ```

      Deze methoden genereren een fout `IllegalArgumentException` als de parameters niet geldig zijn, bijvoorbeeld wanneer:

   * De aanvankelijke buffertijd is minder dan nul.
   * De aanvankelijke buffertijd is groter dan de buffertijd.

1. Gebruik deze `MediaPlayer` methode om de bufferparameterwaarden in te stellen:

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. Gebruik deze `MediaPlayer` methode om de huidige bufferparameterwaarden op te halen:

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Stel bijvoorbeeld de eerste buffer in op 2 seconden en de buffertijd voor het afspelen op 30 seconden:

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

Het `psdkdemo` toont deze eigenschap aan; Gebruik de instellingen van de toepassing om de bufferwaarden in te stellen.
