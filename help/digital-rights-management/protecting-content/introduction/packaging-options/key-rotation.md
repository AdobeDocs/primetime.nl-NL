---
description: 'Wanneer u een pakket maakt, kunt u de volgende coderingsopties selecteren. U kunt de versleutelingsopties echter niet wijzigen tijdens het aanschaffen van licenties '
seo-description: 'Wanneer u een pakket maakt, kunt u de volgende coderingsopties selecteren. U kunt de versleutelingsopties echter niet wijzigen tijdens het aanschaffen van licenties '
seo-title: Toetsrotatie
title: Toetsrotatie
uuid: 6ac3b828-2cd1-42df-b9ee-4daa8e553d5e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Toetsrotatie {#key-rotation}

Wanneer u een pakket maakt, kunt u de volgende coderingsopties selecteren. U kunt de versleutelingsopties echter niet wijzigen tijdens het aanschaffen van licenties:

Tijdens het verpakken wordt inhoud doorgaans versleuteld met de Content Encryption Key (CEK). De client verkrijgt een licentie met de CEK om de inhoud te verbruiken.

Wanneer u sleutelomwenteling toelaat, wordt de Sleutel van de Omwenteling gebruikt om de inhoud te coderen, en de sleutel kan worden veranderd zodat elke Sleutel van de Omwenteling slechts wordt gebruikt om een gedeelte van de inhoud te coderen. De rotatietoetsen zijn beveiligd met de coderingssleutel voor inhoud en de client heeft nog steeds één licentie met de CEK om de inhoud te verbruiken.

Met de implementatie van Packager kunt u bepalen welke coderingssleutel voor inhoud en rotatietoetsen worden gebruikt en hoe vaak de rotatietoetsen worden gewijzigd.

>[!NOTE]
>
>Inhoud die is verpakt met behulp van sleutelrotatie, kan alleen worden afgespeeld op Primetime DRM-clients versie 3.0 of hoger. Oudere clients moeten mogelijk een upgrade uitvoeren om deze inhoud af te spelen.