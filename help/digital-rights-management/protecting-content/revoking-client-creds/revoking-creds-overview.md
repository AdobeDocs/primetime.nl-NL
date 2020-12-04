---
seo-title: Overzicht
title: Overzicht
uuid: c6f54867-d0a3-43fd-9493-6496f1b7831a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Overzicht{#overview}

U moet mogelijk de referenties van een client intrekken of controleren of een bepaalde set referenties al onder bepaalde voorwaarden zijn ingetrokken. Credentials kunnen worden ingetrokken als ze gecompromitteerd zijn. Wanneer deze problemen zich voordoen, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

Adobe handhaaft de lijsten van de Intrekking van het Certificaat (CRLs) voor het terugroepen van gecompromitteerde cliënten. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties te weigeren. Er kan een `RevocationList` worden gemaakt en in de SDK worden doorgegeven om de referenties van de computer in te trekken. Bepaalde DRM/runtime versies kunnen worden ingetrokken op het DRM-beleidsniveau door modulebeperkingen in te stellen in het afspeelrecht of globaal door modulebeperkingen in te stellen in `HandlerConfiguration`.

De discussie is gericht op het intrekken van clientgegevens.
