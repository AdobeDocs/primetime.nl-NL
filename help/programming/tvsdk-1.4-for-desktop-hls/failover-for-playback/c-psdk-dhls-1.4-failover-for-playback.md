---
description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat extern afspelen mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.
seo-description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat extern afspelen mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.
seo-title: Afspelen en failover
title: Afspelen en failover
uuid: 731c087d-9e14-4c7a-a856-c3962b9d7608
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Overzicht {#playback-and-failover-overview}

Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat extern afspelen mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.

Primetime kan niet tegen dergelijke mislukkingen zoals een ISP stroomonderbreking of een kabelontbinding beschermen. Primetime streaming biedt echter bescherming bij uitvalbeveiliging om het afspelen te beschermen tegen bepaalde fouten op de externe server of operationele fouten, waardoor viewers een betere ervaring krijgen. TVSDK implementeert failover-beveiliging om afspeelonderbrekingen tot een minimum te beperken en een naadloze weergave te bereiken ondanks transmissieproblemen. De videospeler schakelt automatisch over naar een back-upmediaset wanneer volledige uitvoeringen of fragmenten niet beschikbaar zijn.
