---
description: Om Flash Player te gebruiken, zorg ervoor dat uw milieu aan de noodzakelijke vereisten voldoet.
title: Flash Player-eisen
exl-id: 26531d0d-d34c-4134-8a05-0604f00a3107
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Flash Player-eisen{#flash-player-requirements}

Om Flash Player te gebruiken, zorg ervoor dat uw milieu aan de noodzakelijke vereisten voldoet.

<!--<a id="section_FEE654D506EC4D85AE77302AD2A27777"></a>-->

Hier volgen de eisen voor de Flash Player:

* Afspelen met `Primetime.js`minimaal Flash Player versie 23 installeren.
* Installeer ten minste Flash Player versie 11.0.0 als u wilt worden gevraagd om updates naar Flash Player versie 23 of hoger.

## Verpakkingsvoorschriften {#section_F95FC1FEEFEA44D28C9596D2F359AFC7}

Voor afspelen met Flash Player zijn de volgende SWF-bestanden vereist:

* Het SWF-hoofdbestand van de toepassing dat Browser TVSDK API&#39;s verwerkt.
* De `playerProductInstall.swf` SWF-bestand dat Flash Player-installatie en -updates afhandelt.

Daarnaast is voor het afspelen van video in Flash een machtigingstoken-bestand vereist dat een SWF of een `.DAT` bestand. U kunt het pad naar de SWF-bestanden, het machtigingstoken-bestand en de naam en het type van het tokenbestand opgeven met de AdobePSDK-API&#39;s.

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
