---
title: Standaard AXS DRM-workflow
description: Standaard AXS DRM-workflow
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Standaard AXS DRM Workflow{#standard-aaxs-drm-workflow}

1. (Pakket) De AXS Java SDK genereert een willekeurige CEK.
1. (Pakket) De CEK wordt gebruikt om inhoud te coderen.
1. (Pakket) CEK wordt gecodeerd gebruikend de openbare sleutel van de Server van de Vergunning AXS.
1. (Pakket) De gecodeerde CEK wordt ingevoegd in de DRM-metagegevens van de inhoud.
1. Het apparaat probeert inhoud af te spelen door een licentie aan te vragen bij de AXS-server.
1. (Licentieverlening) De AXS-server gebruikt de persoonlijke sleutel voor het decoderen van de CEK van de metagegevens.
1. (Licentieverlening) De AXS-server geeft aan het apparaat een licentie af die de CEK bevat.
