---
title: AXS DRM External CEK Workflow
description: Deze workflow is een afwijking van de meeste bestaande DRM-systemen, aangezien hiervoor geen centrale gegevensopslagruimte of CKMS (Content Key Management System) vereist is
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# AXS DRM External CEK Workflow{#aaxs-drm-external-cek-workflow}

Deze workflow is een afwijking van de meeste bestaande DRM-systemen, aangezien hiervoor geen centrale gegevensopslagruimte of CKMS (Content Key Management System) vereist is. Voor klanten die AXS willen gebruiken om met hun bestaande CKMS te werken, biedt AAXS echter een functie met de naam &quot;External CEK&quot;, waarin de CEK extern wordt geleverd op het moment van verpakking en afgifte van licenties.

![](assets/ECEK_Workflow.PNG)

1. (Pakket) De AXS Java SDK wordt geleverd met een CEK- en een CEK-id.
1. (Pakket) De CEK wordt gebruikt om inhoud te coderen.
1. (Pakket) De CEK-id wordt ingevoegd in de DRM-metagegevens van de inhoud.
1. Het apparaat probeert inhoud af te spelen door een licentie aan te vragen bij de AXS-server.
1. (Licentieverlening) De AXS-server extraheert de CEK-id uit de metagegevens van de inhoud.
1. De server AXS wint CEK van CKMS terug.
1. (Licentieverlening) De AXS-server geeft aan het apparaat een licentie af die de CEK bevat.
