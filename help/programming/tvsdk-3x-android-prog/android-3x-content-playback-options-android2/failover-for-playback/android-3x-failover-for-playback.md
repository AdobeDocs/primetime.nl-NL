---
description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal wordt afgespeeld.
title: Afspelen en failover
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Overzicht {#playback-and-failover-overview}

Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal wordt afgespeeld.

>[!IMPORTANT]
>
>Primetime kan niet tegen mislukkingen zoals een ISP stroomonderbreking of een kabelontbinding beschermen.

Primetime streaming biedt bescherming bij uitvalbeveiliging om het afspelen te beschermen tegen bepaalde externe serverfouten of operationele fouten, waardoor u beter kunt zien. Ondanks transmissieproblemen implementeert TVSDK failover-beveiliging om afspeelonderbrekingen te minimaliseren en een naadloze weergave te bereiken. De videospeler schakelt automatisch over naar een back-upmediaset wanneer volledige uitvoeringen of fragmenten niet beschikbaar zijn.