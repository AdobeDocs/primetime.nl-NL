---
description: U kunt client-side en tracking inschakelen door de parameters trackingmode en trackingversion toe te voegen aan uw Bootstrap URL-verzoek.
seo-description: U kunt client-side en tracking inschakelen door de parameters trackingmode en trackingversion toe te voegen aan uw Bootstrap URL-verzoek.
seo-title: Enable client-side ad tracking
title: Enable client-side ad tracking
uuid: 0a825756-1d9a-43c5-bc22-9b366f39fdbb
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Enable client-side ad tracking {#enable-client-side-ad-tracking}

U kunt client-side en tracking inschakelen door de parameters `pttrackingmode` `pttrackingversion` en parameters aan uw Bootstrap URL-aanvraag toe te voegen.

Als de functie voor het bijhouden van gegevens op de client is ingeschakeld, kunt u ook metagegevens ophalen en bijhouden via de URL van de API voor bijhouden. Zie [Zoekparameters](../../msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)voor meer informatie.

Gebruik de URL van de API voor reeksspatiëring voor het bijhouden van advertenties op de client.

1. Voeg de volgende vraagparameters aan het manifestserververzoek URL toe:

   * `pttrackingmode=simple`
   * `pttrackingversion={format version}`

Bijvoorbeeld:

```
https://. . .?. . .&pttrackingmode=simple&pttrackingversion=v1
```
