---
description: De volgende versleutelingsopties worden tijdens het verpakken geselecteerd en kunnen niet worden gewijzigd tijdens het aanschaffen van een licentie.
title: Toetsrotatie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Toetsrotatie{#key-rotation}

De volgende versleutelingsopties worden tijdens het verpakken geselecteerd en kunnen niet worden gewijzigd tijdens het aanschaffen van een licentie.

Tijdens het verpakken wordt de inhoud doorgaans versleuteld met de Content Encryption Key (CEK) en krijgt de client een licentie met de CEK om de inhoud te kunnen gebruiken. Wanneer sleutelrotatie is ingeschakeld, wordt de inhoud versleuteld met de rotatiesleutel. De sleutel kan zodanig worden gewijzigd dat elke rotatiesleutel alleen wordt gebruikt om een deel van de inhoud te versleutelen. De rotatietoetsen zijn beveiligd met de coderingssleutel voor inhoud en de client heeft nog steeds één licentie met de CEK om de inhoud te kunnen gebruiken. Met de implementatie van Packager kunt u bepalen welke coderingssleutel voor inhoud en rotatietoetsen worden gebruikt en hoe vaak de rotatietoetsen worden gewijzigd.

Inhoud die is verpakt met behulp van sleutelrotatie, kan alleen worden afgespeeld op Adobe Access-clients versie 3.0 en hoger. Oudere clients moeten een upgrade uitvoeren om deze inhoud af te spelen.
