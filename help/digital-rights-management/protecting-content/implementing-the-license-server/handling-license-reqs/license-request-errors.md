---
seo-title: Foutafhandeling van licentieaanvraag
title: Foutafhandeling van licentieaanvraag
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Foutafhandeling van licentieaanvraag {#license-request-error-handling}

Als een fout tijdens verzoek het ontleden voorkomt, `HandlerParsingException` komt een voor. Deze uitzondering bevat foutinformatie die aan de client wordt geretourneerd. Als u de fouteninformatie moet terugwinnen, moet u roepen `HandlerParsingException.getErrorData()`. Als een fout optreedt tijdens het genereren van een licentie vanwege DRM-beleidsvereisten waaraan niet is voldaan, `PolicyEvaluationException` treedt een fout op. Deze uitzondering omvat ook `ErrorData` om aan de cliënt terug te keren.

Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` meer informatie over hoe DRM-beleid wordt geëvalueerd tijdens het genereren van licenties.
