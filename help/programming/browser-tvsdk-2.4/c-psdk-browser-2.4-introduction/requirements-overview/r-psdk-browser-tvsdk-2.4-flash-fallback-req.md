---
description: Om Flash Player te gebruiken, zorg ervoor dat uw milieu aan de noodzakelijke vereisten voldoet.
seo-description: Om Flash Player te gebruiken, zorg ervoor dat uw milieu aan de noodzakelijke vereisten voldoet.
seo-title: Flash Player-eisen
title: Flash Player-eisen
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 1%

---


# Flash Player-vereisten{#flash-player-requirements}

Om Flash Player te gebruiken, zorg ervoor dat uw milieu aan de noodzakelijke vereisten voldoet.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Hier volgen de eisen voor de Flash Player:

* Als u wilt afspelen met `Primetime.js`, moet u minstens Flash Player versie 23 installeren.
* Installeer ten minste Flash Player versie 11.0.0 als u wilt worden gevraagd om updates naar Flash Player versie 23 of hoger.

## Verpakkingsvereisten {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Voor afspelen met Flash Player zijn de volgende SWF-bestanden vereist:

* Het SWF-hoofdbestand van de toepassing dat Browser-TVSDK-API&#39;s afhandelt.
* Het SWF-bestand `playerProductInstall.swf` dat de installatie en updates van Flash Player afhandelt.

Daarnaast is voor het afspelen van video in Flash een machtigingstoken-bestand nodig dat een SWF- of `.DAT`-bestand kan zijn. Het pad naar de SWF-bestanden, het machtigingstoken-bestand en de naam en het type van het tokenbestand kunnen worden opgegeven met de AdobePSDK-API&#39;s.

Bijvoorbeeld:

```js
// Set relative or http path to directory containing SWF.  
// Defaults to current directory for the html page. 
AdobePSDK.setSWFPath(<swfPath>); 
 
// Set the relative or http path to directory containing token file(s). 
// Defaults to SWFPath + "token/". 
AdobePSDK.setAuthorizationTokenPath(<authorizationTokenPath>); 
 
// Set the name of the token file, do not include any path in this string. 
AdobePSDK.setAuthorizationTokenFilename("hlsaf_localhost.swf"); 
 
//Set the token type, "DAT" or "SWF". Defaults to "DAT" 
AdobePSDK.setAuthorizationTokenType("SWF");
```

