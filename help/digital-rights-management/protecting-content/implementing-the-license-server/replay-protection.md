---
seo-title: Replay-beveiliging
title: Replay-beveiliging
uuid: c737998a-9c33-48b4-b741-91106697d71f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Replay-beveiliging{#replay-protection}

Voor de bescherming van het afspelen, kunt u willen controleren of bericht herkenningsteken onlangs door te roepen is gezien `RequestMessageBase.getMessageId()`. Als dat het geval is, probeert een aanvaller mogelijk het verzoek opnieuw af te spelen. Dit moet worden geweigerd. Om herhalingspogingen te ontdekken, kan de server een lijst van onlangs gezien berichtherkenningstekens opslaan en elk inkomend verzoek tegen de caching lijst controleren. Om de hoeveelheid tijd te beperken moet de berichtherkenningstekens worden opgeslagen, vraag `HandlerConfiguration.setTimestampTolerance()`. Als dit bezit wordt geplaatst, ontkent SDK dan om het even welk verzoek dat een timestamp voor meer dan het gespecificeerde aantal seconden van de servertijd draagt.
