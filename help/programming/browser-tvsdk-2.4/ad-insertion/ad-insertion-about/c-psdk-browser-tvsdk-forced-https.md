---
title: Beveiligd laden van advertentie via HTTPS
description: Beveiligd laden van advertentie via HTTPS
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Beveiligd laden van advertentie via HTTPS{#secure-ad-loading-over-https}

Adobe Primetime kan externe advertentieservers via https aanvragen, zelfs als de speler wordt gehost op http. Alleen die aanroepen op advertentieservers worden bijgewerkt naar https die de client zoekt tijdens de Auditude en oplossingfase.

>[!NOTE]
>
>Deze functie wordt niet ondersteund voor Flash.

Gebruik het volgende om veilig en ladend toe te laten. Deze optie is niet standaard ingeschakeld.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
