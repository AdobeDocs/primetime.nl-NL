---
description: 302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.
title: HTTP 302-herleidingsoptimalisatie
exl-id: 80d5d38d-c998-4fc0-b527-b38e578d76e7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# HTTP 302-herleidingsoptimalisatie {#http-redirect-optimization}

302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.

Als een hoofdmanifestverzoek wordt omgeleid, en optimalisering 302 in uw speler wordt toegelaten, zullen de verdere verzoeken die voor activa van dat manifest worden gemaakt de definitieve domeinplaats gebruiken, die extra 302 reacties vermijdt. Deze functie is standaard ingeschakeld en u kunt deze instelling wijzigen.

>[!IMPORTANT]
>
>Deze functie wordt alleen ondersteund in gecertificeerde browsers die de `responseURL` eigenschap in de `XMLHttpRequest` object.

Voor Flash fallback, herinner de volgende informatie:

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
