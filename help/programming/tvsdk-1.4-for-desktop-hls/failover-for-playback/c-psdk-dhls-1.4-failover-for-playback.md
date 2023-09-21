---
description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.
title: Afspelen en failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Overzicht {#playback-and-failover-overview}

Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal worden afgespeeld.

Primetime kan niet tegen dergelijke mislukkingen zoals een ISP stroomonderbreking of een kabelontbinding beschermen. Primetime streaming biedt echter bescherming bij uitvalbeveiliging om het afspelen te beschermen tegen bepaalde fouten op de externe server of operationele fouten, waardoor viewers een betere ervaring krijgen. TVSDK implementeert failover-beveiliging om afspeelonderbrekingen tot een minimum te beperken en een naadloze weergave te bereiken ondanks transmissieproblemen. De videospeler schakelt automatisch over naar een back-upmediaset wanneer volledige uitvoeringen of fragmenten niet beschikbaar zijn.
