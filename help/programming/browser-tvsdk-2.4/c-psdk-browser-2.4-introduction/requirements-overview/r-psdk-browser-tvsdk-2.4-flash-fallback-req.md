---
description: Als u Flash Player wilt gebruiken, moet u ervoor zorgen dat uw omgeving aan de vereiste vereisten voldoet.
seo-description: Als u Flash Player wilt gebruiken, moet u ervoor zorgen dat uw omgeving aan de vereiste vereisten voldoet.
seo-title: Flash Player-vereisten
title: Flash Player-vereisten
uuid: f181457b-2bb4-4baa-b2b7-d787f65fab75
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Flash Player-vereisten{#flash-player-requirements}

Als u Flash Player wilt gebruiken, moet u ervoor zorgen dat uw omgeving aan de vereiste vereisten voldoet.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Hier volgen de vereisten voor Flash Player:

* Installeer ten minste Flash Player versie 23 om af te spelen met `Primetime.js`.
* Installeer ten minste Flash Player versie 11.0.0 als u wilt worden gevraagd om updates van Flash Player versie 23 of hoger.

## Verpakkingsvoorschriften {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Voor afspelen met Flash Player zijn de volgende SWF-bestanden vereist:

* Het SWF-hoofdbestand van de toepassing dat Browser-TVSDK-API&#39;s afhandelt.
* Het `playerProductInstall.swf` SWF-bestand dat de installatie en updates van Flash Player afhandelt.

Daarnaast is voor het afspelen van video in Flash een machtigingstoken-bestand nodig, dat een SWF- of `.DAT` bestandsbestand kan zijn. Het pad naar de SWF-bestanden, het machtigingstoken-bestand en de naam en het type van het tokenbestand kunnen worden opgegeven met de AdobePSDK-API&#39;s.

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

