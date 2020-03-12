---
description: Er zijn API's die u kunnen helpen Adobe Flash Player te gebruiken.
seo-description: Er zijn API's die u kunnen helpen Adobe Flash Player te gebruiken.
seo-title: Nuttige API's voor Adobe Flash Player
title: Nuttige API's voor Adobe Flash Player
uuid: eae314c0-fd9e-480f-ae1c-9b5f3eb4db4b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Nuttige API&#39;s voor Adobe Flash Player{#helpful-apis-for-the-adobe-flash-player}

Er zijn API&#39;s die u kunnen helpen Adobe Flash Player te gebruiken.

## AdobePSDK.MediaResource {#section_8C339FA1386D4B1A926A1459B2619E5E}

```js
new MediaResource(url, type, metadata, forceFlash)
```

Indien ondersteund, kunt u de `forceFlash` parameter gebruiken om de determinatiereeks voor de afspeeltechnologie te negeren en de implementatie dwingen de Flash Player te gebruiken.

<!--<a id="section_FEE3205B532446498771F7DD55B5E79F"></a>-->

```js
AdobePSDK.PlayerTechnology = { 
/** 
* Determine the {AdobePSDK.PlayerTechnology} that would be used for the given 
* media resource. 
* @param {AdobePSDK.MediaResource} mediaResource 
* @returns {AdobePSDK.PlayerTechnology.Type} 
*/ 
getSupportedTechnology(mediaResource); 
}; 
 
AdobePSDK.PlayerTechnology.Type = {  
MSE, 
VIDEO_TAG,  
FLASH,  
UNKNOWN 
}; 
 
/** 
* Set the path to the SWF relative to the main html page or using http URL. 
* Defaults to the current directory of the html page. 
* 
* @param swfPath 
*/ 
AdobePSDK.setSWFPath(swfPath); 
 
/** 
* Set the path to the folder containing the authorization token(s). 
* If not set, defaults to the token folder within the SWFPath: SWFPath + "token/". 
* @param authorizationTokenPath 
*/ 
AdobePSDK.setAuthorizationTokenPath(authorizationTokenPath); 
 
/** 
* Set the name of the authorization token file. Defaults to "hlsAF_localhost.dat". 
* @param authorizationTokenFileName 
*/ 
AdobePSDK.setAuthorizationTokenFilename(authorizationTokenFilename); 
 
/** 
* Set the authorization token type, can be "SWF" or "DAT". Defaults to "DAT" 
* @param {String} authorizationTokenType 
*/ 
AdobePSDK.setAuthorizationTokenType(authorizationTokenType);
```

