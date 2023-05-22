---
title: Foutafhandeling van licentieaanvraag
description: Foutafhandeling van licentieaanvraag
copied-description: true
exl-id: 7cfdebc5-db2b-4629-98e6-31ad71cb424c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Foutafhandeling van licentieaanvraag {#license-request-error-handling}

Als een fout optreedt tijdens het parseren van een aanvraag, voert u een `HandlerParsingException` voorkomt. Deze uitzondering bevat foutinformatie die aan de client wordt geretourneerd. Als u de fouteninformatie moet terugwinnen, moet u roepen `HandlerParsingException.getErrorData()`. Als een fout optreedt tijdens het genereren van een licentie vanwege DRM-beleidsvereisten waaraan niet is voldaan, kan een `PolicyEvaluationException` voorkomt. Deze uitzondering omvat ook `ErrorData` aan de client worden geretourneerd.

Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` voor meer informatie over hoe DRM-beleid wordt geëvalueerd tijdens het genereren van licenties.
