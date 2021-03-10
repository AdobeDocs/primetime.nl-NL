---
title: Overzicht van op tijd gebaseerde regels
description: Overzicht van op tijd gebaseerde regels
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Op tijd gebaseerde regels {#time-based-rules}

Primetime DRM gebruikt &#39;zachte handhaving&#39; van op tijd gebaseerde licentiebeperkingen. Als een tijdrecht tijdens het afspelen van een video verloopt, is het standaardgedrag van Primetime DRM om het afspelen niet te beperken tot de volgende keer dat de videostream opnieuw wordt gemaakt (door `Netstream.stop()` en `Netstream.play()` aan te roepen).

Terwijl de zachte handhaving het standaardgedrag is, kunt u harde handhaving ook toelaten door één van de volgende taken uit te voeren:

* Zorg dat uw videospeler de licentie periodiek opvraagt om er zeker van te zijn dat geen van de tijdbeperkingen is verlopen. Dit kan worden verwezenlijkt door `DRMManager.loadVoucher(LOCAL_ONLY).` te roepen een foutencode wijst erop dat de lokaal-opgeslagen vergunning niet meer geldig is.
* Wanneer de gebruiker **[!UICONTROL Pause]** klikt, kunt u de huidige videotijdstempel opnemen en dan `Netstream.stop()` roepen. Wanneer de gebruiker de knoop van het Spel klikt, kunt u aan de geregistreerde plaats zoeken en dan `Netstream.play()` roepen.