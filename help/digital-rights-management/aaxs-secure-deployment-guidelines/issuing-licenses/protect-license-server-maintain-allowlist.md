---
title: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
description: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden {#maintain-a-allowlist-of-trusted-content-packagers}

An **lijst van gewenste personen** is een lijst met vertrouwde entiteiten. In het geval van inhoudspakketten zijn dit organisaties die door de eigenaar van de inhoud worden vertrouwd om de FLV/F4V-videobestanden te verpakken (of te coderen) en met DRM beveiligde inhoud te maken. Bij het implementeren van Adobe Access wordt u aangeraden een lijst van gewenste personen van vertrouwde inhoudspakketten bij te houden en de identiteit te verifiëren van de inhoudspakker in de DRM-metagegevens (de DRM-header) van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Ga voor meer informatie over het ophalen van informatie over de entiteit die de inhoud in een pakket heeft opgenomen naar `V2ContentMetaData.getPackagerInfo()` in de *API-naslaggids voor Adobe*.
