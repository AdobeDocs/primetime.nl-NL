---
seo-title: Replay-beveiliging
title: Replay-beveiliging
uuid: 75f2be65-b2fc-428a-b853-34a4b30960ce
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Replay-beveiliging{#replay-protection}

Voor replay bescherming, kan het verstandig zijn om te controleren of de bericht herkenningsteken onlangs door het roepen is gezien `RequestMessageBase.getMessageId()`. Als dat het geval is, probeert een aanvaller mogelijk het verzoek opnieuw af te spelen. Dit moet worden geweigerd. Om herhalingspogingen te ontdekken, kan de server een lijst van onlangs gezien berichtherkenningstekens opslaan en elk inkomend verzoek tegen de caching lijst controleren. Om de hoeveelheid tijd te beperken moet de berichtherkenningstekens worden opgeslagen, vraag `HandlerConfiguration.setTimestampTolerance()`. Als dit bezit wordt geplaatst, zal SDK om het even welk verzoek ontkennen dat een timestamp meer dan het gespecificeerde aantal seconden van de servertijd draagt.
