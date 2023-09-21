---
description: Klanten kunnen DRM (Adobe Access, AXS) gebruiken met hun eigen CKMS (Content Key Management Systems) met de functie External CEK.
title: Adobe Access DRM External CEK Overview
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Adobe Access DRM External CEK Overview {#adobe-access-drm-external-cek-overview}

Klanten kunnen DRM (Adobe Access, AXS) gebruiken met hun eigen CKMS (Content Key Management Systems) met de functie External CEK.

DRM van de Toegang van de Adobe (AXS), door gebrek, onttrekt de behoefte om sleutels, certificaten, en meta-gegevens direct te behandelen DRM tijdens het inhoudspakketproces. De AXS Java SDK genereert automatisch een CEK (random Content Encryption Key) tijdens het verpakken en gebruikt deze om de inhoud te coderen. Vervolgens codeert de SDK de CEK zelf en voegt deze in de metagegevens van de inhoud in. Tijdens de licentieafgifte heeft de AXS-server alleen de persoonlijke sleutel van de AAXS-licentieserver nodig om toegang te krijgen tot de CEK van de metagegevens om een licentie te genereren.
