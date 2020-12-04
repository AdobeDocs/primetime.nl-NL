---
description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal wordt afgespeeld.
seo-description: Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal wordt afgespeeld.
seo-title: Afspelen en failover
title: Afspelen en failover
uuid: 511f16b9-2b86-42c1-8d89-09b26534200b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Overzicht {#playback-and-failover-overview}

Streaming via internet vereist een constante en stabiele verbinding om een stream vanaf een externe server af te spelen. De variabiliteit van de internetverbinding of het afspelen van streaming van een viewer betekent echter dat het afspelen op afstand mogelijk niet de kwaliteit heeft van media die lokaal wordt afgespeeld.

>[!IMPORTANT]
>
>Primetime kan niet tegen mislukkingen zoals een ISP stroomonderbreking of een kabelontbinding beschermen.

Primetime streaming biedt bescherming bij uitvalbeveiliging om het afspelen te beschermen tegen bepaalde externe serverfouten of operationele fouten, waardoor u beter kunt zien. Ondanks transmissieproblemen implementeert TVSDK failover-beveiliging om afspeelonderbrekingen te minimaliseren en een naadloze weergave te bereiken. De videospeler schakelt automatisch over naar een back-upmediaset wanneer volledige uitvoeringen of fragmenten niet beschikbaar zijn.