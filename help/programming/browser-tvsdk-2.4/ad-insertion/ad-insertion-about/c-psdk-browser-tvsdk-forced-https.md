---
title: Beveiligd laden van advertentie via HTTPS
description: Beveiligd laden van advertentie via HTTPS
copied-description: true
exl-id: d43418e9-631b-4344-a5b3-0a6154a325d4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Beveiligd laden van advertentie via HTTPS{#secure-ad-loading-over-https}

Adobe Primetime kan externe advertentieservers via https aanvragen, zelfs als de speler wordt gehost op http. Alleen die aanroepen op advertentieservers worden bijgewerkt naar https waar de client naar zoekt tijdens de Auditude Ad resolver-fase.

>[!NOTE]
>
>Deze functie wordt niet ondersteund voor Flash.

Gebruik het volgende om veilig en ladend toe te laten. Deze optie is niet standaard ingeschakeld.

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
