---
title: Kritiek op DRM-beleid
description: Kritiek op DRM-beleid
copied-description: true
exl-id: b9f5a095-9ec4-4ad7-8b70-9abae72d2a86
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Kritiek op DRM-beleid{#drm-policy-criticality}

Als u van plan bent om nieuwe gebruiksregels in een beleid toe te passen DRM, en als u van plan bent om dit beleid DRM in inhoud te gebruiken die voor oudere vergunningsservers (en daarom niet correct de nieuwe gebruiksregels interpreteert) is verpakt, kunt u moeten specificeren hoe de oudere vergunningsservers zich moeten gedragen. Standaard is de DRM-beleidsnrioriteit ingesteld op `true`.

Deze instelling geeft aan dat de licentieserver alle onderdelen van het DRM-beleid moet verwerken voordat een licentie kan worden gegenereerd die het opgegeven DRM-beleid gebruikt. Als de kritiek op het DRM-beleid is ingesteld op `false`, kan een oudere licentieserver die onderdelen van het DRM-beleid negeren die niet correct kunnen worden geïnterpreteerd. Daarom omvatten om het even welke vergunningen die door de server worden geproduceerd geen nieuwe gebruiksregels.

Primetime DRM-servers die versie 2.0.2 van de SDK ondersteunen of later de instelling voor de kritische instelling van het DRM-beleid accepteren.
