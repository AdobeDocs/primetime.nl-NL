---
seo-title: Standaard AXS DRM-workflow
title: Standaard AXS DRM-workflow
description: Standaard AXS DRM-workflow
seo-description: Standaard AXS DRM-workflow
uuid: b996eb2c-8e37-4a29-a972-e09c69d2461d
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Standaard AXS DRM Workflow{#standard-aaxs-drm-workflow}

1. (Pakket) De AXS Java SDK genereert een willekeurige CEK.
1. (Pakket) De CEK wordt gebruikt om inhoud te coderen.
1. (Pakket) CEK wordt gecodeerd gebruikend de openbare sleutel van de Server van de Vergunning AXS.
1. (Pakket) De gecodeerde CEK wordt ingevoegd in de DRM-metagegevens van de inhoud.
1. Het apparaat probeert inhoud af te spelen door een licentie aan te vragen bij de AXS-server.
1. (Licentieverlening) De AXS-server gebruikt de persoonlijke sleutel voor het decoderen van de CEK van de metagegevens.
1. (Licentieverlening) De AXS-server geeft het apparaat een licentie met de CEK.
