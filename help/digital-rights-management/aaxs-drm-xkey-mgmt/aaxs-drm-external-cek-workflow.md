---
seo-title: AXS DRM External CEK Workflow
title: AXS DRM External CEK Workflow
description: Deze workflow is een afwijking van de meeste bestaande DRM-systemen, aangezien hiervoor geen centrale gegevensopslagruimte of CKMS (Content Key Management System) vereist is
seo-description: Deze workflow is een afwijking van de meeste bestaande DRM-systemen, aangezien hiervoor geen centrale gegevensopslagruimte of CKMS (Content Key Management System) vereist is
uuid: b313594b-0feb-4f27-bf02-f04b955e2140
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc

---


# AXS DRM External CEK Workflow{#aaxs-drm-external-cek-workflow}

Deze workflow is een afwijking van de meeste bestaande DRM-systemen, aangezien hiervoor geen centrale gegevensopslagruimte of CKMS (Content Key Management System) vereist is. Voor klanten die AXS willen gebruiken om met hun bestaande CKMS te werken, biedt AAXS echter een functie met de naam &quot;External CEK&quot;, waarin de CEK extern wordt geleverd op het moment van verpakking en afgifte van licenties.

![](assets/ECEK_Workflow.PNG)

1. (Pakket) De AXS Java SDK wordt voorzien van een CEK en een CEK ID.
1. (Pakket) De CEK wordt gebruikt om inhoud te coderen.
1. (Pakket) De CEK-id wordt ingevoegd in de DRM-metagegevens van de inhoud.
1. Het apparaat probeert inhoud af te spelen door een licentie aan te vragen bij de AXS-server.
1. (Licentieverlening) De AXS-server extraheert de CEK-id uit de metagegevens van de inhoud.
1. De server AXS wint CEK van CKMS terug.
1. (Licentieverlening) De AXS-server geeft aan het apparaat een licentie af die de CEK bevat.
