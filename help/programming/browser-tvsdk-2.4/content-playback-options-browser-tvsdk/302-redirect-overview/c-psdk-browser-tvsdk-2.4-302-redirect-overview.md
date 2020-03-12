---
description: 302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.
seo-description: 302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.
seo-title: HTTP 302-herleidingsoptimalisatie
title: HTTP 302-herleidingsoptimalisatie
uuid: d3009c6c-320a-4c0f-b6ba-bf6473049823
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# HTTP 302-herleidingsoptimalisatie {#http-redirect-optimization}

302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.

Als een hoofdmanifestverzoek wordt omgeleid, en optimalisering 302 in uw speler wordt toegelaten, zullen de verdere verzoeken die voor activa van dat manifest worden gemaakt de definitieve domeinplaats gebruiken, die extra 302 reacties vermijdt. Deze functie is standaard ingeschakeld en u kunt deze instelling wijzigen.

>[!IMPORTANT]
>
>Deze functie wordt alleen ondersteund in gecertificeerde browsers die de `responseURL` eigenschap in het `XMLHttpRequest` object ondersteunen.

Houd rekening met de volgende informatie voor Flash-fallback:

* Uw eindgebruikers moeten Adobe Flash Player versie 23 of hoger hebben geïnstalleerd.
* Als de streamintegriteit is uitgeschakeld, wordt 302 omleiding alleen ondersteund door gecertificeerde browsers.

## 302-herleidingsoptimalisatie uitschakelen {#disabling-redirect-optimization}

Met de eigenschap useRedirectedUrl kunt u 302 omleiden (true) of uitschakelen (false).

Bijvoorbeeld:

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
