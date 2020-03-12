---
description: 'null'
seo-description: 'null'
seo-title: Beveiligd laden van advertentie via HTTPS
title: Beveiligd laden van advertentie via HTTPS
uuid: 10657f59-cfbf-4c75-9249-fc154952bc51
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

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
