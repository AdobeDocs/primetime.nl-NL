---
description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt configureren hoe de speler buffert.
seo-description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt configureren hoe de speler buffert.
seo-title: Bufferen
title: Bufferen
uuid: c84b98ed-0070-4a86-a409-d7702e5be23c
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Overzicht {#buffering-overview}

Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt configureren hoe de speler buffert.

TVSDK definieert een bufferlengte van minimaal 30 seconden en een eerste buffertijd voordat de media worden afgespeeld, van minimaal 2 seconden. Nadat `play` door de toepassing is aangeroepen, maar voordat het afspelen begint, buffert TVSDK de media tot de begintijd om een vloeiende start te geven wanneer deze daadwerkelijk wordt afgespeeld.

U kunt de buffertijden wijzigen door een nieuw bufferbeleid te definiëren en u kunt wijzigen wanneer de eerste buffering plaatsvindt door onmiddellijk aan te gebruiken.

## Het buffertijdbeleid {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

Afhankelijk van uw omgeving (inclusief het apparaat, het besturingssysteem of de netwerkvoorwaarden) kunt u verschillende bufferbeleidsregels voor de speler instellen, zoals het wijzigen van de minimale duur voor initiële buffering en voor doorlopende buffering bij het afspelen.

Nadat u `play` roept, begint de media speler het bufferen van de video. Wanneer de mediaspeler de hoeveelheid video heeft gebufferd die door de eerste buffertijd is opgegeven, wordt het afspelen gestart. Dit proces verbetert de opstarttijd omdat de speler niet wacht tot de gehele afspeelbuffer is gevuld voordat het afspelen wordt gestart. In plaats daarvan begint het afspelen nadat de paar eerste seconden zijn gebufferd.

Terwijl de video wordt teruggegeven, blijft TVSDK nieuwe fragmenten bufferen tot het is als buffer opgetreden voor de hoeveelheid die door de tijd van de playbackbuffer wordt gespecificeerd. Als de huidige bufferlengte onder de tijd van de playbackbuffer zakt, zal de speler extra fragmenten downloaden. Zodra de huidige bufferlengte een paar seconden boven de tijd van de playbackbuffer is, zal TVSDK ophouden met het downloaden van fragmenten.

>[!TIP]
>
>Als de aanvankelijke bufferwaarde hoog is, zou het uw gebruiker een lange aanvankelijke buffertijd kunnen geven alvorens te beginnen. Hierdoor wordt het afspelen langer soepel afgespeeld. als de netwerkvoorwaarden echter slecht zijn , kan het afspelen eerst worden vertraagd .

Als u onmiddellijk toelaat door `prepareBuffer` te roepen, begint het aanvankelijke bufferen op dat ogenblik, in plaats van het wachten op `play`.

## Buffertijden {#section_05CDD927869D47EBA1D2069B1416B2E4} instellen

`MediaPlayer` verstrekt methodes om de aanvankelijke buffertijd en playbackbuffertijd te plaatsen en te krijgen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

1. Stel het object `BufferControlParameters` in, dat de initiële parameters voor buffertijd en tijd van de afspeelbuffer inkapselt.

   Deze klasse biedt de volgende fabrieksmethoden:

   * De eerste buffertijd instellen op gelijk aan de buffertijd van het afspelen:

      ```
      public static BufferControlParameters createSimple(long bufferTime)
      ```

   * De tijd van de eerste buffer en de afspeelbuffer instellen:

      ```
      public static BufferControlParameters createDual( 
        long initialBuffer,  
        long bufferTime)
      ```
   Als de parameters ongeldig zijn, werpen deze methodes `MediaPlayerException` met foutencode `PSDKErrorCode.INVALID_ARGUMENT`, zoals wanneer de volgende voorwaarden worden voldaan:

   * De aanvankelijke buffertijd is minder dan nul.
   * De aanvankelijke buffertijd is groter dan de buffertijd.


1. Als u de waarden van de bufferparameters wilt instellen, gebruikt u deze methode `MediaPlayer`:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Als u de huidige bufferparameterwaarden wilt ophalen, gebruikt u deze `MediaPlayer`-methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

Stel bijvoorbeeld de eerste buffer in op 5 seconden en de buffertijd voor het afspelen op 30 seconden:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
