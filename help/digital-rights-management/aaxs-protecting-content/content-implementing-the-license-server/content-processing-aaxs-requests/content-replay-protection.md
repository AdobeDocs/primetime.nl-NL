---
title: Replay-beveiliging
description: Replay-beveiliging
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# Herafspeelbeveiliging{#replay-protection}

Voor replay bescherming, kan het verstandig zijn om te controleren of de bericht herkenningsteken onlangs door `RequestMessageBase.getMessageId()` te roepen is gezien. Als dat het geval is, probeert een aanvaller mogelijk het verzoek opnieuw af te spelen. Dit moet worden geweigerd. Om herhalingspogingen te ontdekken, kan de server een lijst van onlangs gezien berichtherkenningstekens opslaan en elk inkomend verzoek tegen de caching lijst controleren. Om de hoeveelheid tijd te beperken moet de berichtherkenningstekens worden opgeslagen, vraag `HandlerConfiguration.setTimestampTolerance()`. Als dit bezit wordt geplaatst, zal SDK om het even welk verzoek ontkennen dat een timestamp meer dan het gespecificeerde aantal seconden van de servertijd draagt.
