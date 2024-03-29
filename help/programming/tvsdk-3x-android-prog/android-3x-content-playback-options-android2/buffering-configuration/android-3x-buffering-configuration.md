---
description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt configureren hoe de speler buffert.
title: Bufferen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Overzicht {#buffering-overview}

Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt configureren hoe de speler buffert.

TVSDK definieert een bufferlengte van minimaal 30 seconden en een eerste buffertijd voordat de media worden afgespeeld, van minimaal 2 seconden. Nadat de toepassing is aangeroepen `play`Maar voordat het afspelen begint, buffert TVSDK de media tot de begintijd zodat het afspelen probleemloos begint.

U kunt de buffertijden wijzigen door een nieuw bufferbeleid te definiëren en u kunt wijzigen wanneer de eerste buffering plaatsvindt door onmiddellijk aan te gebruiken.

## Tijdbeleid bufferen {#section_9B3407D52F1E4CB48E7A4836EBDA8F70}

Afhankelijk van uw omgeving (inclusief het apparaat, het besturingssysteem of de netwerkvoorwaarden) kunt u verschillende bufferbeleidsregels voor de speler instellen, zoals het wijzigen van de minimale duur voor initiële buffering en voor doorlopende buffering bij het afspelen.

Nadat u hebt gebeld `play`De mediaspeler begint de video te bufferen. Wanneer de mediaspeler de hoeveelheid video heeft gebufferd die door de eerste buffertijd is opgegeven, wordt het afspelen gestart. Dit proces verbetert de opstarttijd omdat de speler niet wacht tot de gehele afspeelbuffer is gevuld voordat het afspelen wordt gestart. In plaats daarvan begint het afspelen nadat de paar eerste seconden zijn gebufferd.

Terwijl de video wordt teruggegeven, blijft TVSDK nieuwe fragmenten bufferen tot het is als buffer opgetreden voor de hoeveelheid die door de tijd van de playbackbuffer wordt gespecificeerd. Als de huidige bufferlengte onder de tijd van de playbackbuffer zakt, zal de speler extra fragmenten downloaden. Zodra de huidige bufferlengte een paar seconden boven de tijd van de playbackbuffer is, zal TVSDK ophouden met het downloaden van fragmenten.

>[!TIP]
>
>Als de aanvankelijke bufferwaarde hoog is, zou het uw gebruiker een lange aanvankelijke buffertijd kunnen geven alvorens te beginnen. Dit kan een langere afspeeltijd voor een vloeiende weergave zorgen. Als de netwerkvoorwaarden echter slecht zijn, kan de eerste afspeelbewerking worden vertraagd.

Als u onmiddellijk toelaat op door te roepen `prepareBuffer`De eerste buffering begint op dat moment, in plaats van te wachten op `play`.

## Buffertijden instellen {#section_05CDD927869D47EBA1D2069B1416B2E4}

De `MediaPlayer` biedt methoden voor het instellen en ophalen van de eerste buffertijd en de buffertijd voor het afspelen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

1. Stel de `BufferControlParameters` object, dat de initiële parameters voor buffertijd en afspeelbuffertijd inkapselt.

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

   Als de parameters niet geldig zijn, genereren deze methoden `MediaPlayerException` met foutcode `PSDKErrorCode.INVALID_ARGUMENT`, bijvoorbeeld wanneer aan de volgende voorwaarden is voldaan:

   * De aanvankelijke buffertijd is minder dan nul.
   * De aanvankelijke buffertijd is groter dan de buffertijd.

1. Als u de bufferparameters wilt instellen, gebruikt u deze `MediaPlayer` methode:

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. Als u de huidige bufferparameterwaarden wilt ophalen, gebruikt u deze `MediaPlayer` methode:

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

<!--<a id="example_DE0580B3AD404635825D3301C1F096B6"></a>-->

Stel bijvoorbeeld de eerste buffer in op 5 seconden en de buffertijd voor het afspelen op 30 seconden:

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(5000, 30000));
```
