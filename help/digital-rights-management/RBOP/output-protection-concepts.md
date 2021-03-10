---
description: Deze sectie verstrekt een conceptueel overzicht van de configuratie, de opties, en betekenissen verbonden aan outputbescherming.
title: RBOP-concepten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# RBOP-concepten {#rbop-concepts}

Deze sectie verstrekt een conceptueel overzicht van de configuratie, de opties, en betekenissen verbonden aan outputbescherming.

U geeft uw vereisten voor op resolutie gebaseerde uitvoerbeveiliging op in een hiërarchische JSON-structuur. *De uitvoervereisten zijn gebaseerd op pixels.*

Op het hoogste niveau van de specificatie JSON, kunt u maximumpixelresolutie, en pixelbeperkingen voor gespecificeerde resoluties bepalen:

* `maxPixel` - De maximale pixelresolutie definieert de maximale resolutie waarvoor decodering wordt uitgevoerd.
* `pixelConstraints` - Met pixelbeperkingen worden uitvoervereisten gedefinieerd die voor een opgegeven resolutie moeten worden afgedwongen.

U koppelt uitvoervereisten aan specifieke pixelbeperkingen. De typen vereisten die u kunt koppelen aan een bepaalde pixelbeperking zijn onder andere beperkingen voor digitale, analoge en over-the-air (OTA) verbindingen.

**Digitale uitvoer**

Met de vereiste digitale uitvoer kunt u restrictieve opties instellen, zoals &#39;Digitale uitvoerbeveiliging is vereist&#39; of &#39;Afspelen is niet toegestaan&#39;. Uitvoervereisten kunnen ook minder restrictieve opties specificeren, zoals &quot;geen bescherming zou moeten worden toegepast&quot; of &quot;digitale bescherming zou moeten worden gebruikt als het beschikbaar is.&quot;

**Analoge uitvoer**

Analoge uitvoerverbindingen zijn eenvoudiger dan digitale uitvoer. zij bestaan uit één uitvoervereiste.
