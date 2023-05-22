---
title: Standaard AXS DRM-workflow
description: Standaard AXS DRM-workflow
exl-id: 3bc6aa6a-cda6-4c83-af08-f27eb103a47a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
