---
description: Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.
seo-description: Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.
seo-title: Adobe Access DRM - Overzicht externe CEK
title: Adobe Access DRM - Overzicht externe CEK
uuid: ea0bba63-7743-4216-863f-392500998eb6
translation-type: tm+mt
source-git-commit: 92e04cbb5e94f60c8d06e94b826ff9361c10ef97
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Adobe Access DRM External CEK Overview {#adobe-access-drm-external-cek-overview}

Klanten kunnen Adobe Access (AAXS) DRM met hun eigen CKMS (Content Key Management Systems) gebruiken met de functie External CEK.

Adobe Access (AXS) DRM, standaard, onttrekt de behoefte om sleutels, certificaten, en meta-gegevens direct te behandelen DRM tijdens het inhoudspakketproces. De AXS Java SDK genereert automatisch een CEK (random Content Encryption Key) tijdens het verpakken en gebruikt deze om de inhoud te coderen. Vervolgens codeert de SDK de CEK zelf en voegt deze in de metagegevens van de inhoud in. Tijdens de licentieafgifte heeft de AXS-server alleen de persoonlijke sleutel van de AAXS-licentieserver nodig om toegang te krijgen tot de CEK van de metagegevens om een licentie te genereren.
