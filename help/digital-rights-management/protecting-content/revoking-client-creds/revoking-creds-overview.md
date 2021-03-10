---
title: Overzicht
description: Overzicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Overzicht{#overview}

U moet mogelijk de referenties van een client intrekken of controleren of een bepaalde set referenties al onder bepaalde voorwaarden zijn ingetrokken. Credentials kunnen worden ingetrokken als ze gecompromitteerd zijn. Wanneer deze problemen zich voordoen, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

Adobe handhaaft de lijsten van de Intrekking van het Certificaat (CRLs) voor het terugroepen van gecompromitteerde cliënten. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties te weigeren. Er kan een `RevocationList` worden gemaakt en in de SDK worden doorgegeven om de referenties van de computer in te trekken. Bepaalde DRM/runtime versies kunnen worden ingetrokken op het DRM-beleidsniveau door modulebeperkingen in te stellen in het afspeelrecht of globaal door modulebeperkingen in te stellen in `HandlerConfiguration`.

De discussie is gericht op het intrekken van clientgegevens.
