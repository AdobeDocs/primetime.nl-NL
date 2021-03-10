---
description: Er zijn enkele beperkingen en een aantal problemen in de manier waarop de truc-afspeelmodus zich gedraagt.
title: Beperkingen en gedrag voor het spelen van truc
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Beperkingen en gedrag voor het spelen van truc{#limitations-and-behavior-for-trick-play}

Er zijn enkele beperkingen en een aantal problemen in de manier waarop de truc-afspeelmodus zich gedraagt.

<!--<a id="section_8B88E281A0FA4661B4C2C70A0ABED57C"></a>-->

Hier volgen de beperkingen voor de modus voor het spelen van truc:

* De master afspeellijst moet alleen I-frame-segmenten bevatten. Alleen de keyframes van de I-frame track worden op het scherm weergegeven.
* De audiotrack en gesloten bijschriften zijn uitgeschakeld.
* De logica voor de adaptieve bitsnelheid (ABR) is uitgeschakeld. TVSDK selecteert één beetjetarief tussen het laagste verstrekte tarief en 800 kbps en gebruikt dat tarief tijdens de volledige truc-spelzitting.
* Afspelen en pauzeren zijn ingeschakeld.
* Seek is niet toegestaan. Als u wilt zoeken, roept u `pause` aan om de speelmodus voor truc af te sluiten en vervolgens `seek` aan te roepen.

* U kunt van truc spelwijze in om het even welk toegestaan playbacktarief (spel of pauze) gaan.
* Wanneer advertenties in de stream worden opgenomen:

   * U kunt alleen truc spelen tijdens het afspelen van de hoofdinhoud. Er wordt een fout verzonden wanneer u probeert om het afspelen tijdens een advertentie-einde te truien.
   * Nadat de truc-afspeelmodus is gestart, worden add-einden genegeerd en worden er geen advertentiegebeurtenissen geactiveerd.
   * De tijdlijn die door TVSDK aan de spelertoepassing wordt blootgesteld, wordt niet gewijzigd, zelfs niet als ad-einden worden overgeslagen.
   * De huidige tijdwaarde springt vooruit (op snelle voorwaartse) of achteruit (op snelle terugspoeling) met de duur overgeslagen en onderbreking. Door dit spronggedrag voor de huidige tijd kan de streamduur ongewijzigd blijven tijdens het spelen van een truc. Uw spelertoepassing kan de lokale tijdwaarde krijgen om de tijd met betrekking tot slechts de belangrijkste inhoud te volgen. Er worden geen tijdsprongen uitgevoerd op de waarden die tijdens het overslaan van een advertentie worden geretourneerd.
   * De gebeurtenis `MediaPlayerEvent.AD_BREAK_SKIPPED` wordt verzonden vlak voordat een advertentieeinde wordt overgeslagen. De speler kan deze gebeurtenis gebruiken om aangepaste logica te implementeren met betrekking tot overgeslagen en verbroken bewerkingen.
   * Als u een truc afsluit, wordt hetzelfde ad-playbackbeleid aangeroepen als wanneer u een zoekopdracht afsluit.

      Daarom hangt het gedrag, net als bij het zoeken, af van het feit of het afspeelbeleid van uw toepassing afwijkt van het standaardbeleid. Standaard wordt het laatste overgeslagen en afgebroken geluid afgespeeld op het punt waar u de speelmodus hebt verlaten.

