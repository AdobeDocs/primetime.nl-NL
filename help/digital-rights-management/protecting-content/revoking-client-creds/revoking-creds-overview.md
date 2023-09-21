---
title: Overzicht
description: Overzicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Overzicht{#overview}

U moet mogelijk de referenties van een client intrekken of controleren of een bepaalde set referenties al onder bepaalde voorwaarden zijn ingetrokken. Credentials kunnen worden ingetrokken als ze gecompromitteerd zijn. Wanneer deze problemen zich voordoen, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

De Adobe handhaaft de Lijsten van de Intrekking van Certificaat (CRLs) voor het terugroepen van gecompromitteerde cliënten. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties niet toe te staan. A `RevocationList` kan worden gemaakt en doorgegeven aan de SDK om de referenties van de computer in te trekken. Specifieke DRM/runtime versies kunnen op DRM-beleidsniveau worden ingetrokken door modulebeperkingen in te stellen in het afspeelrecht of globaal door modulebeperkingen in te stellen in het dialoogvenster `HandlerConfiguration`.

De discussie is gericht op het intrekken van clientgegevens.
