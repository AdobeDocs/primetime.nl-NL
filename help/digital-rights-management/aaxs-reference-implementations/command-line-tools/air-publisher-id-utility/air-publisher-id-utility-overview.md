---
title: Overzicht van het hulpprogramma AIR Publisher ID
description: Overzicht van het hulpprogramma AIR Publisher ID
copied-description: true
exl-id: ad982ec8-0180-4185-8752-08592cabef3d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Overzicht van het hulpprogramma AIR Publisher ID {#air-publisher-id-utility-overview}

Tijdens het maken van een AIR-bestand genereert ADT (AIR Developer Tool) een uitgevers-id. Dit is een unieke id voor het certificaat waarmee het AIR-bestand is gemaakt. Als u hetzelfde certificaat opnieuw gebruikt voor meerdere AIR-toepassingen, hebben deze dezelfde uitgevers-id. Het hulpprogramma AIR Publisher-id wordt gebruikt om de uitgevers-id voor een AIR-toepassing te berekenen. AIR-releases na 1.5.2 schrijven de gegenereerde uitgevers-id niet naar een bestand. Het is dus noodzakelijk dit gereedschap te gebruiken om de uitgevers-id te bepalen als u een AIR-lijst van gewenste personen gebruikt.

>[!NOTE]
>
>De uitgevers-id, die wordt gebruikt voor de handhaving van de AIR-lijst van gewenste personen, is niet dezelfde als de uitgevers-id die door de uitgever van de toepassing is opgegeven [!DNL application.xml] bestand.
