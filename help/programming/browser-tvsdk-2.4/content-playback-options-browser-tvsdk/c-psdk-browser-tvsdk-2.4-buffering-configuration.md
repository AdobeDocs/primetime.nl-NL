---
description: Voor een vloeiender kijkervaring wordt de videostream soms door Browser-TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
title: Bufferen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# Bufferen{#buffering}

Voor een vloeiender kijkervaring wordt de videostream soms door Browser-TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.

Browser TVSDK bepaalt een lengte van de playbackbuffer van minstens 30 seconden en een aanvankelijke buffertijd binnen dat, alvorens de media begint te spelen, van minstens 2 seconden. Nadat de toepassing is aangeroepen `play` Maar voordat het afspelen begint, buffert Browser-TVSDK de media tot de begintijd zodat het afspelen probleemloos begint.

## Buffertijden instellen {#section_179DA7CA865D48EBA4B03D50B6B7BC50}

De MediaPlayer biedt methoden om de initiële buffertijd en de buffertijd voor het afspelen in te stellen en op te halen.

>[!TIP]
>
>Als u de bufferbesturingsparameters niet instelt voordat u begint met afspelen, wordt de mediaspeler standaard ingesteld op 2 seconden voor de eerste buffer en op 30 seconden voor de doorlopende buffertijd.

* Als u de bufferparameters wilt gebruiken, gebruikt u de MediaPlayer `bufferControlParameters` kenmerk.

  Stel bijvoorbeeld de eerste buffer in op 2 seconden en de buffertijd voor het afspelen op 30 seconden:

  ```js
  var params = new AdobePSDK.BufferControlParameters(2000, 30000);
  ```

## Tijdbeleid bufferen {#section_7EF2947931654CCC8DAB9172391FA4EB}

Afhankelijk van uw omgeving (inclusief het apparaat, het besturingssysteem of de netwerkvoorwaarden) kunt u verschillende bufferbeleidsregels voor de speler instellen, zoals het wijzigen van de minimale duur voor initiële buffering en voor doorlopende buffering bij het afspelen.

Nadat u hebt gebeld `play`De mediaspeler begint de video te bufferen. Wanneer de mediaspeler de hoeveelheid video heeft gebufferd die door de eerste buffertijd is opgegeven, wordt het afspelen gestart. Dit proces verbetert de opstarttijd omdat de speler niet wacht tot de gehele afspeelbuffer is gevuld voordat het afspelen wordt gestart. In plaats daarvan begint het afspelen nadat de paar eerste seconden zijn gebufferd.

Terwijl de video wordt teruggegeven, blijft Browser TVSDK nieuwe fragmenten bufferen tot het is als buffer opgetreden voor de hoeveelheid die door de tijd van de playbackbuffer wordt gespecificeerd. Als de huidige bufferlengte onder de tijd van de playbackbuffer zakt, zal de speler extra fragmenten downloaden. Wanneer de huidige bufferlengte enkele seconden boven de buffertijd voor afspelen ligt, wordt het downloaden van fragmenten door Browser-TVSDK gestopt.

>[!TIP]
>
>Als de aanvankelijke bufferwaarde hoog is, zou het uw gebruiker een lange aanvankelijke buffertijd kunnen geven alvorens te beginnen. Dit kan een langere afspeeltijd voor een vloeiende weergave zorgen. Als de netwerkvoorwaarden echter slecht zijn, kan de eerste afspeelbewerking worden vertraagd.
