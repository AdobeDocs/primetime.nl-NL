---
description: Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.
title: Adobe Access DRM - Overzicht externe CEK
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Adobe Access DRM External CEK Overview {#adobe-access-drm-external-cek-overview}

Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.

Adobe Access (AXS) DRM, standaard, onttrekt de behoefte om sleutels, certificaten, en meta-gegevens direct te behandelen DRM tijdens het inhoudspakketproces. De AXS Java SDK genereert automatisch een CEK (random Content Encryption Key) tijdens het verpakken en gebruikt deze om de inhoud te coderen. Vervolgens codeert de SDK de CEK zelf en voegt deze in de metagegevens van de inhoud in. Tijdens de licentieafgifte heeft de AXS-server alleen de persoonlijke sleutel van de AAXS-licentieserver nodig om toegang te krijgen tot de CEK van de metagegevens om een licentie te genereren.
