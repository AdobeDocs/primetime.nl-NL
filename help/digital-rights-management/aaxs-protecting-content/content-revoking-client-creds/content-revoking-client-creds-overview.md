---
title: Klantenreferenties intrekken
description: Klantenreferenties intrekken
copied-description: true
exl-id: 583dff28-c34a-4759-81a6-0471feab309f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Klantenreferenties intrekken{#revoking-client-credentials}

Onder bepaalde omstandigheden is het noodzakelijk de geloofsbrieven van een cliënt terug te trekken of te controleren of een bepaalde reeks geloofsbrieven reeds zijn ingetrokken. Credentials kunnen worden ingetrokken als de referenties worden gewijzigd. Als dit gebeurt, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

Adobe handhaaft de lijsten van de Intrekking van het Certificaat (CRLs) voor het terugroepen van gecompromitteerde cliënten. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties te weigeren. A `RevocationList` kan worden gemaakt en doorgegeven aan de SDK om de referenties van de computer in te trekken. Specifieke DRM/runtime versies kunnen worden ingetrokken op beleidsniveau (door modulebeperkingen in te stellen in het afspeelrecht) of op algemeen niveau (door modulebeperkingen in te stellen in het dialoogvenster `HandlerConfiguration`).

De bespreking in dit hoofdstuk zal zich op het intrekken van cliëntgeloofsbrieven concentreren.
