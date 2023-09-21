---
title: Klantenreferenties intrekken
description: Klantenreferenties intrekken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Klantenreferenties intrekken{#revoking-client-credentials}

Onder bepaalde omstandigheden is het noodzakelijk de geloofsbrieven van een cliënt terug te trekken of te controleren of een bepaalde reeks geloofsbrieven reeds zijn ingetrokken. Credentials kunnen worden ingetrokken als de referenties worden gewijzigd. Als dit gebeurt, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

De Adobe handhaaft de Lijsten van de Intrekking van Certificaat (CRLs) voor het terugroepen van gecompromitteerde cliënten. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties niet toe te staan. A `RevocationList` kan worden gemaakt en doorgegeven aan de SDK om de referenties van de computer in te trekken. Specifieke DRM/runtime versies kunnen worden ingetrokken op beleidsniveau (door modulebeperkingen in te stellen in het afspeelrecht) of op algemeen niveau (door modulebeperkingen in te stellen in het dialoogvenster `HandlerConfiguration`).

De bespreking in dit hoofdstuk zal zich op het intrekken van cliëntgeloofsbrieven concentreren.
