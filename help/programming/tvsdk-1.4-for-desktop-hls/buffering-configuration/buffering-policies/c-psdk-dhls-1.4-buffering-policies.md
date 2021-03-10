---
description: Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.
title: Tijdbeleid bufferen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# Het buffertijdbeleid {#buffering-time-policies}

Voor een vloeiender kijkervaring wordt de videostream soms door TVSDK gebufferd. U kunt de manier configureren waarop de speler buffert.

TVSDK definieert een bufferlengte van minimaal 30 seconden en een eerste buffertijd binnen die tijd, voordat de media worden afgespeeld, van minimaal 5 seconden. Nadat `play` door de toepassing is aangeroepen, maar voordat het afspelen begint, buffert TVSDK de media tot de begintijd om een vloeiende start te geven wanneer deze daadwerkelijk wordt afgespeeld.

U kunt de buffertijden wijzigen door een nieuw bufferbeleid te definiëren.

<!--<a id="section_F6EEE15600814A70A57CCBACE20D68BD"></a>-->

Afhankelijk van uw omgeving (inclusief het apparaat, het besturingssysteem of de netwerkvoorwaarden) kunt u verschillende bufferbeleidsregels voor de speler instellen, zoals het wijzigen van de minimale duur voor initiële buffering en voor doorlopende buffering bij het afspelen.

Nadat u `play` roept, begint de media speler het bufferen van de video. Wanneer de mediaspeler de hoeveelheid video heeft gebufferd die door de eerste buffertijd is opgegeven, wordt het afspelen gestart. Dit proces verbetert de opstarttijd omdat de speler niet wacht tot de gehele afspeelbuffer is gevuld voordat het afspelen wordt gestart. In plaats daarvan begint het afspelen nadat de paar eerste seconden zijn gebufferd.

Terwijl de video wordt teruggegeven, blijft TVSDK nieuwe fragmenten bufferen tot het is als buffer opgetreden voor de hoeveelheid die door de tijd van de playbackbuffer wordt gespecificeerd. Als de huidige bufferlengte onder de tijd van de playbackbuffer zakt, zal de speler extra fragmenten downloaden. Zodra de huidige bufferlengte een paar seconden boven de tijd van de playbackbuffer is, zal TVSDK ophouden met het downloaden van fragmenten.

>[!TIP]
>
>Als de aanvankelijke bufferwaarde hoog is, zou het uw gebruiker een lange aanvankelijke buffertijd kunnen geven alvorens te beginnen. Hierdoor wordt het afspelen langer soepel afgespeeld. als de netwerkvoorwaarden echter slecht zijn , kan het afspelen eerst worden vertraagd .

