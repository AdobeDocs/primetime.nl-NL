---
seo-title: Foutafhandeling van licentieaanvraag
title: Foutafhandeling van licentieaanvraag
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Foutafhandeling van licentieverzoek {#license-request-error-handling}

Als een fout tijdens verzoek het ontleden voorkomt, `HandlerParsingException` komt voor. Deze uitzondering bevat foutinformatie die aan de client wordt geretourneerd. Als u de fouteninformatie moet terugwinnen, moet u `HandlerParsingException.getErrorData()` roepen. Als een fout optreedt tijdens het genereren van een licentie vanwege DRM-beleidsvereisten waaraan niet is voldaan, treedt een `PolicyEvaluationException` op. Deze uitzondering omvat ook `ErrorData` die naar de client moet worden geretourneerd.

Zie de API-documentatie voor `LicenseRequestMessage.generateLicense()` voor meer informatie over hoe DRM-beleid wordt geëvalueerd tijdens het genereren van licenties.
