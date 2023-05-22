---
title: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
description: Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden
copied-description: true
exl-id: 4c296d23-75c1-4d0b-a636-31b49e99c753
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden {#maintain-a-allowlist-of-trusted-content-packagers}

An **lijst van gewenste personen** is een lijst met vertrouwde entiteiten. In het geval van inhoudspakketten zijn dit organisaties die door de eigenaar van de inhoud worden vertrouwd om de FLV/F4V-videobestanden te verpakken (of te coderen) en met DRM beveiligde inhoud te maken. Wanneer u Adobe Access implementeert, wordt u aangeraden een lijst van gewenste personen vertrouwde inhoudspakketten bij te houden en de identiteit te verifiëren van de inhoudsverpakker in de DRM-metagegevens (de DRM-header) van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Ga voor meer informatie over het ophalen van informatie over de entiteit die de inhoud in een pakket heeft opgenomen naar `V2ContentMetaData.getPackagerInfo()` in de *Referentie voor Adobe Access API*.
