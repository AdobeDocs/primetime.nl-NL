---
description: U kunt het bijhouden van advertenties aan de clientzijde inschakelen door de parameters trackingmode en trackingversion toe te voegen aan de URL-aanvraag van de Bootstrap.
title: Enable client-side ad tracking
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# Enable client-side ad tracking {#enable-client-side-ad-tracking}

U kunt het bijhouden van advertenties op de client inschakelen door het `pttrackingmode` en `pttrackingversion` parameters voor uw Bootstrap URL-aanvraag.

Als de functie voor het bijhouden van gegevens op de client is ingeschakeld, kunt u ook metagegevens ophalen en bijhouden via de URL van de API voor bijhouden. Zie voor meer informatie [Zoekparameters](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md).

Gebruik de URL van de API voor reeksspatiëring voor het bijhouden van advertenties op de client.

1. Voeg de volgende vraagparameters aan het manifestserververzoek URL toe:

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Bijvoorbeeld:

```URL
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
