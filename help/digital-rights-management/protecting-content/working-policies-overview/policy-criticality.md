---
title: Kritiek op DRM-beleid
description: Kritiek op DRM-beleid
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Kritiek op DRM-beleid{#drm-policy-criticality}

Als u van plan bent om nieuwe gebruiksregels in een beleid toe te passen DRM, en als u van plan bent om dit beleid DRM in inhoud te gebruiken die voor oudere vergunningsservers (en daarom niet correct de nieuwe gebruiksregels interpreteert) is verpakt, kunt u moeten specificeren hoe de oudere vergunningsservers zich moeten gedragen. Standaard is de DRM-beleidstrentekst ingesteld op `true`.

Deze instelling geeft aan dat de licentieserver alle onderdelen van het DRM-beleid moet verwerken voordat een licentie kan worden gegenereerd die het opgegeven DRM-beleid gebruikt. Als de kritiek op het DRM-beleid is ingesteld op `false`, kan een oudere licentieserver de onderdelen van het DRM-beleid negeren die niet correct kunnen worden geïnterpreteerd. Daarom omvatten om het even welke vergunningen die door de server worden geproduceerd geen nieuwe gebruiksregels.

Primetime DRM-servers die versie 2.0.2 van de SDK ondersteunen of later de instelling voor de kritische instelling van het DRM-beleid accepteren.
