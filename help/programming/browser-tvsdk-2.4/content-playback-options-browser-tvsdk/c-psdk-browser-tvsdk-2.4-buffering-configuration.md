---
description: Voor een vloeiender kijkervaring wordt de videostream soms door Browser-TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
seo-description: Voor een vloeiender kijkervaring wordt de videostream soms door Browser-TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
seo-title: Bufferen
title: Bufferen
uuid: 9937731d-013e-41e9-a4c9-f7a54a5e654d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---


# Buffering{#buffering}

Voor een vloeiender kijkervaring wordt de videostream soms door Browser-TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.

Browser TVSDK bepaalt een lengte van de playbackbuffer van minstens 30 seconden en een aanvankelijke buffertijd binnen dat, alvorens de media begint te spelen, van minstens 2 seconden. Nadat de toepassing `play` maar alvorens playback begint, buffert Browser TVSDK de media tot de aanvankelijke tijd om een vlotte aanvang te geven wanneer het eigenlijk begint te spelen.

## Buffertijden {#section_179DA7CA865D48EBA4B03D50B6B7BC50} instellen

De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

* Om de bufferparameters te gebruiken, gebruik het `bufferControlParameters` attribuut van MediaPlayer.

   Stel bijvoorbeeld de eerste buffer in op 2 seconden en de buffertijd voor het afspelen op 30 seconden:

   ```js
   var params = new AdobePSDK.BufferControlParameters(2000, 30000);
   ```

## Het buffertijdbeleid {#section_7EF2947931654CCC8DAB9172391FA4EB}

Afhankelijk van uw omgeving (inclusief het apparaat, het besturingssysteem of de netwerkvoorwaarden) kunt u verschillende bufferbeleidsregels voor de speler instellen, zoals het wijzigen van de minimale duur voor initiële buffering en voor doorlopende buffering bij het afspelen.

Nadat u `play` roept, begint de media speler het bufferen van de video. Wanneer de mediaspeler de hoeveelheid video heeft gebufferd die door de eerste buffertijd is opgegeven, wordt het afspelen gestart. Dit proces verbetert de opstarttijd omdat de speler niet wacht tot de gehele afspeelbuffer is gevuld voordat het afspelen wordt gestart. In plaats daarvan begint het afspelen nadat de paar eerste seconden zijn gebufferd.

Terwijl de video wordt teruggegeven, blijft Browser TVSDK nieuwe fragmenten bufferen tot het is als buffer opgetreden voor de hoeveelheid die door de tijd van de playbackbuffer wordt gespecificeerd. Als de huidige bufferlengte onder de tijd van de playbackbuffer zakt, zal de speler extra fragmenten downloaden. Wanneer de huidige bufferlengte enkele seconden boven de buffertijd voor afspelen ligt, wordt het downloaden van fragmenten door Browser-TVSDK gestopt.

>[!TIP]
>
>Als de aanvankelijke bufferwaarde hoog is, zou het uw gebruiker een lange aanvankelijke buffertijd kunnen geven alvorens te beginnen. Hierdoor wordt het afspelen langer soepel afgespeeld. als de netwerkvoorwaarden echter slecht zijn , kan het afspelen eerst worden vertraagd .

