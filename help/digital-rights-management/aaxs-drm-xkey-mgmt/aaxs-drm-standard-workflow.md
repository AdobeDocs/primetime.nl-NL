---
title: Standaard AXS DRM-workflow
description: Standaard AXS DRM-workflow
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Standaard AXS DRM-workflow{#standard-aaxs-drm-workflow}

1. (Pakket) De AXS Java SDK genereert een willekeurige CEK.
1. (Pakket) De CEK wordt gebruikt om inhoud te coderen.
1. (Pakket) CEK wordt gecodeerd gebruikend de openbare sleutel van de Server van de Vergunning AXS.
1. (Pakket) De gecodeerde CEK wordt ingevoegd in de DRM-metagegevens van de inhoud.
1. Het apparaat probeert inhoud af te spelen door een licentie aan te vragen bij de AXS-server.
1. (Licentieverlening) De AXS-server gebruikt de persoonlijke sleutel voor het decoderen van de CEK van de metagegevens.
1. (Licentieverlening) De AXS-server geeft het apparaat een licentie met de CEK.
