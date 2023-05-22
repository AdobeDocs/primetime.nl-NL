---
title: Overzicht van op tijd gebaseerde regels
description: Overzicht van op tijd gebaseerde regels
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Op tijd gebaseerde regels {#time-based-rules}

Primetime DRM gebruikt &#39;zachte handhaving&#39; van op tijd gebaseerde licentiebeperkingen. Als een tijdrecht tijdens het afspelen van een video verloopt, is het standaardgedrag van Primetime DRM dat het afspelen niet wordt beperkt tot de volgende keer dat de videostream opnieuw wordt gemaakt (door `Netstream.stop()` en `Netstream.play()`).

Terwijl de zachte handhaving het standaardgedrag is, kunt u harde handhaving ook toelaten door één van de volgende taken uit te voeren:

* Zorg dat uw videospeler de licentie periodiek opvraagt om er zeker van te zijn dat geen van de tijdbeperkingen is verlopen. Dit kan door te roepen worden verwezenlijkt `DRMManager.loadVoucher(LOCAL_ONLY).` Een foutcode geeft aan dat de lokaal opgeslagen licentie niet langer geldig is.
* Wanneer de gebruiker klikt **[!UICONTROL Pause]**, kunt u de huidige video timestamp opnemen en dan roepen `Netstream.stop()`. Wanneer de gebruiker de knoop van het Spel klikt, kunt u aan de geregistreerde plaats zoeken en dan roepen `Netstream.play()`.