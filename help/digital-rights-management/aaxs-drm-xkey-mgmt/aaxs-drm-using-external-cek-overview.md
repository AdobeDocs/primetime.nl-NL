---
description: Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.
title: Adobe Access DRM - Overzicht externe CEK
exl-id: 4131863b-5773-4222-aae9-d984267cdb86
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Adobe Access DRM - Overzicht externe CEK {#adobe-access-drm-external-cek-overview}

Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.

Adobe Access (AXS) DRM, standaard, onttrekt de behoefte om sleutels, certificaten, en meta-gegevens direct te behandelen DRM tijdens het inhoudspakketproces. De AXS Java SDK genereert automatisch een CEK (random Content Encryption Key) tijdens het verpakken en gebruikt deze om de inhoud te coderen. Vervolgens codeert de SDK de CEK zelf en voegt deze in de metagegevens van de inhoud in. Tijdens de licentieafgifte heeft de AXS-server alleen de persoonlijke sleutel van de AAXS-licentieserver nodig om toegang te krijgen tot de CEK van de metagegevens om een licentie te genereren.
