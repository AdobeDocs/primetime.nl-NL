---
title: Primetime DRM op de client
description: Primetime DRM op de client
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# Primetime DRM op de client{#primetime-drm-on-the-client}

Een Primetime-TVSDK-toepassing die beveiligde inhoud afspeelt, moet eerst Primetime DRM-API&#39;s oproepen om de workflow te starten voor het gebruik van licenties en het afspelen van beveiligde inhoud. In deze workflow construeert Primetime DRM op de client een licentieaanvraag van de metagegevens van de beveiligde inhoud en verzendt het vervolgens naar de Primetime DRM-licentieserver.

Voordat u de licentieaanvraag afgeeft, kan de klant desgewenst de vereiste verificatie/verificatie uitvoeren (afhankelijk van uw bedrijfsregels).
