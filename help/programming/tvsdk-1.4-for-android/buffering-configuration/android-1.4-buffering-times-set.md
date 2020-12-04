---
description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
seo-description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
seo-title: Buffertijden instellen
title: Buffertijden instellen
uuid: 5a3945a4-1935-4797-b19d-84989850a487
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---


# Bufferen {#buffering}

Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.

TVSDK definieert een bufferlengte van minimaal 30 seconden en een eerste buffertijd binnen die periode, voordat de media worden afgespeeld, van minimaal 2 seconden. Nadat `play` door de toepassing is aangeroepen, maar voordat het afspelen begint, buffert TVSDK de media tot de begintijd om een vloeiende start te geven wanneer deze daadwerkelijk wordt afgespeeld.

U kunt de buffertijden wijzigen door een nieuw bufferbeleid te definiëren en u kunt wijzigen wanneer de eerste buffering plaatsvindt met instant-on.

## Buffertijden {#set-buffering-times} instellen

`MediaPlayer` verstrekt methodes om de aanvankelijke buffertijd en playbackbuffertijd te plaatsen en te krijgen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

1. Stel het object `BufferControlParameters` in, waarin de parameters voor de aanvankelijke buffertijd en de tijd van de afspeelbuffer worden ingekapseld:

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

1. Als u de parameterwaarden voor de buffer wilt instellen, gebruikt u deze methode `MediaPlayer`:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Als u de huidige bufferparameterwaarden wilt ophalen, gebruikt u deze `MediaPlayer`-methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   Als de AVE de opgegeven waarden niet kan instellen, voert de mediaspeler de status `ERROR` in met de foutcode `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

Stel bijvoorbeeld de eerste buffer in op 2 seconden en de buffertijd voor het afspelen op 30 seconden:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Deze functie wordt geïllustreerd door de implementatie van de Primetime-referentie. Gebruik de instellingen van de toepassing om de bufferwaarden in te stellen.