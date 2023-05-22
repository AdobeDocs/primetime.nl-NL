---
title: Replay-beveiliging
description: Replay-beveiliging
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Replay-beveiliging{#replay-protection}

Voor afspeelbeveiliging kunt u controleren of de bericht-id onlangs is bekeken door `RequestMessageBase.getMessageId()`. Als dat het geval is, probeert een aanvaller mogelijk het verzoek opnieuw af te spelen. Dit moet worden geweigerd. Om herhalingspogingen te ontdekken, kan de server een lijst van onlangs gezien berichtherkenningstekens opslaan en elk inkomend verzoek tegen de caching lijst controleren. Om de hoeveelheid tijd te beperken moet de berichtherkenningstekens worden opgeslagen, vraag `HandlerConfiguration.setTimestampTolerance()`. Als dit bezit wordt geplaatst, ontkent SDK dan om het even welk verzoek dat een timestamp voor meer dan het gespecificeerde aantal seconden van de servertijd draagt.
