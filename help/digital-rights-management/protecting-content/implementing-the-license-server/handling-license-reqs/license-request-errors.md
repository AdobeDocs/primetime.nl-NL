---
title: Foutafhandeling van licentieaanvraag
description: Foutafhandeling van licentieaanvraag
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Foutafhandeling van licentieaanvraag {#license-request-error-handling}

Als een fout optreedt tijdens het parseren van een aanvraag, voert u een `HandlerParsingException` voorkomt. Deze uitzondering bevat foutinformatie die aan de client wordt geretourneerd. Als u de foutinformatie moet ophalen, moet u `HandlerParsingException.getErrorData()`. Als een fout optreedt tijdens het genereren van een licentie vanwege DRM-beleidsvereisten waaraan niet is voldaan, kan een `PolicyEvaluationException` voorkomt. Deze uitzondering omvat ook `ErrorData` aan de client worden geretourneerd.

Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` voor meer informatie over hoe DRM-beleid wordt geëvalueerd tijdens het genereren van licenties.
