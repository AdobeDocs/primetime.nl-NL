---
seo-title: Klantenreferenties intrekken
title: Klantenreferenties intrekken
uuid: 47f1ec1a-bd8f-4f8c-bee3-bfbf6d9902e7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Klantenreferenties intrekken{#revoking-client-credentials}

Onder bepaalde omstandigheden is het noodzakelijk de geloofsbrieven van een cliënt terug te trekken of te controleren of een bepaalde reeks geloofsbrieven reeds zijn ingetrokken. Credentials kunnen worden ingetrokken als de referenties worden gewijzigd. Als dit gebeurt, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

Adobe handhaaft de lijsten van de Intrekking van het Certificaat (CRLs) voor het terugroepen van gecompromitteerde cliënten. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties te weigeren. Er kan een `RevocationList` worden gemaakt en in de SDK worden doorgegeven om de referenties van de computer in te trekken. Specifieke DRM/runtime versies kunnen worden ingetrokken op beleidsniveau (door modulebeperkingen in te stellen in het afspeelrecht) of globaal (door modulebeperkingen in te stellen in `HandlerConfiguration`).

De bespreking in dit hoofdstuk zal zich op het intrekken van cliëntgeloofsbrieven concentreren.
