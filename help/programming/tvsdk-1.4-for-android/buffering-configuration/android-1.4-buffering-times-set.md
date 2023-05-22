---
description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
title: Buffertijden instellen
exl-id: 4542d10a-b6f8-430d-8b9a-5a358d1c0e9d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Bufferen {#buffering}

Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.

TVSDK definieert een bufferlengte van minimaal 30 seconden en een eerste buffertijd binnen die periode, voordat de media worden afgespeeld, van minimaal 2 seconden. Nadat de toepassing is aangeroepen `play` Maar voordat het afspelen begint, buffert TVSDK de media tot de begintijd zodat het afspelen probleemloos begint.

U kunt de buffertijden wijzigen door een nieuw bufferbeleid te definiëren en u kunt wijzigen wanneer de eerste buffering plaatsvindt met instant-on.

## Buffertijden instellen {#set-buffering-times}

De `MediaPlayer` biedt methoden voor het instellen en ophalen van de eerste buffertijd en de buffertijd voor het afspelen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

1. Stel de `BufferControlParameters` object, dat de initiële parameters voor buffertijd en afspeelbuffertijd inkapselt:

       Deze klasse biedt twee fabrieksmethoden:
   
   * De eerste buffertijd instellen op gelijk aan de buffertijd van het afspelen:

      ```java
      public static BufferControlParameters createSimple( 
          long bufferTime)
      ```

   * U stelt als volgt de buffertijden voor initialen en afspelen in:

      ```java
      public static BufferControlParameters createDual( 
          long initialBuffer,   
          long bufferTime)
      ```

      Deze methoden genereren een `IllegalArgumentException` als de parameters niet geldig zijn, bijvoorbeeld wanneer:

   * De aanvankelijke buffertijd is minder dan nul.
   * De aanvankelijke buffertijd is groter dan de buffertijd.

1. Gebruik deze optie om de bufferparameterwaarden in te stellen `MediaPlayer` methode:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Als u de huidige bufferparameterwaarden wilt ophalen, gebruikt u deze `MediaPlayer` methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   Als de AVE de opgegeven waarden niet kan instellen, voert de mediaspeler de `ERROR` status met de foutcode `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Stel bijvoorbeeld de eerste buffer in op 2 seconden en de buffertijd voor het afspelen op 30 seconden:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Deze functie wordt geïllustreerd door de implementatie van de Primetime-referentie. Gebruik de instellingen van de toepassing om de bufferwaarden in te stellen.
