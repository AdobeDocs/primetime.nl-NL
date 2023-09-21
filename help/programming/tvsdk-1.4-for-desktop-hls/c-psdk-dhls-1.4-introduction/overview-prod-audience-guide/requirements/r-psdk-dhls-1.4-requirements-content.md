---
description: Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests), inclusief DRM-coderingssleutels.
title: Inhoud- en manifestvereisten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Inhoud- en manifestvereisten {#content-and-manifest-requirements}

Controleer de beperkingen en vereisten voor streams en afspeellijsten (manifests), inclusief DRM-coderingssleutels.

| Opnemen en instellen `RESOLUTION` eigenschap voor elke ABR-stream in het manifestbestand. U moet Flash Player 14 of later gebruiken. |
|---|
| Als de DRM-beveiligde stream meerdere bitsnelheden (MBR) heeft, moet de DRM-coderingssleutel die voor de MBR wordt gebruikt, gelijk zijn aan de sleutel die in alle bitsnelheidstreams wordt gebruikt. |
| Moet dezelfde bitsnelheidvertoningen hebben als de uitvoeringen van de hoofdinhoud. |
