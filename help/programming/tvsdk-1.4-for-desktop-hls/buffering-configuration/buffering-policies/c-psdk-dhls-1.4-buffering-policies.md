---
description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
title: Tijdbeleid bufferen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Tijdbeleid bufferen {#buffering-time-policies}

Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.

TVSDK definieert een bufferlengte van minimaal 30 seconden en een eerste buffertijd binnen die tijd, voordat de media worden afgespeeld, van minimaal 5 seconden. Nadat de toepassing is aangeroepen `play` Maar voordat het afspelen begint, buffert TVSDK de media tot de begintijd zodat het afspelen probleemloos begint.

U kunt de buffertijden wijzigen door een nieuw bufferbeleid te definiëren.

<!--<a id="section_F6EEE15600814A70A57CCBACE20D68BD"></a>-->

Afhankelijk van uw omgeving (inclusief het apparaat, het besturingssysteem of de netwerkvoorwaarden) kunt u verschillende bufferbeleidsregels voor de speler instellen, zoals het wijzigen van de minimale duur voor initiële buffering en voor doorlopende buffering bij het afspelen.

Nadat u hebt gebeld `play`De mediaspeler begint de video te bufferen. Wanneer de mediaspeler de hoeveelheid video heeft gebufferd die door de eerste buffertijd is opgegeven, wordt het afspelen gestart. Dit proces verbetert de opstarttijd omdat de speler niet wacht tot de gehele afspeelbuffer is gevuld voordat het afspelen wordt gestart. In plaats daarvan begint het afspelen nadat de paar eerste seconden zijn gebufferd.

Terwijl de video wordt teruggegeven, blijft TVSDK nieuwe fragmenten bufferen tot het is als buffer opgetreden voor de hoeveelheid die door de tijd van de playbackbuffer wordt gespecificeerd. Als de huidige bufferlengte onder de tijd van de playbackbuffer zakt, zal de speler extra fragmenten downloaden. Zodra de huidige bufferlengte een paar seconden boven de tijd van de playbackbuffer is, zal TVSDK ophouden met het downloaden van fragmenten.

>[!TIP]
>
>Als de aanvankelijke bufferwaarde hoog is, zou het uw gebruiker een lange aanvankelijke buffertijd kunnen geven alvorens te beginnen. Dit kan een langere afspeeltijd voor een vloeiende weergave zorgen. Als de netwerkvoorwaarden echter slecht zijn, kan de eerste afspeelbewerking worden vertraagd.
