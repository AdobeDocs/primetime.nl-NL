---
description: Met de volgende nieuwe API's kunt u DRM-callbacks definiëren.
title: DRM-callbacks implementeren
exl-id: 3aaa502d-9273-4320-a022-642fee75dafd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# DRM-callbacks implementeren{#implementing-drm-callbacks}

Met de volgende nieuwe API&#39;s kunt u DRM-callbacks definiëren.

<!--<a id="section_1090BFDB2C1D4EA4AAC9F9A6EC9DCD51"></a>-->

U kunt een callback-functie definiëren (bijvoorbeeld `parseContentIdCallback`) om de inhoud-id te parseren en in te stellen op `drmManager` door `setParseContentIdCallback` API.

```js
var arrayToString = function (array) { 
        var uint16array = new Uint16Array(array.buffer); 
        return String.fromCharCode.apply(null, uint16array); 
}, 
  
parseContentIdCallback = function (initData) { 
        var contentId = arrayToString(initData), 
            tokens = contentId?contentId.split('/'):[]; 
        if(tokens.length) { 
            return tokens[tokens.length-1]; 
        } else { 
            return ''; 
        } 
}; 
   
drmManager.setParseContentIdCallback(parseContentIdCallback);
```

<!--<a id="section_1E082B428EA74D9CA11C052158A83947"></a>-->

U kunt een callback-functie definiëren (bijvoorbeeld `onCertificateResponseCallback`) om een reactie van het tekstcertificaat te verwerken en de functie in te stellen op `drmManager` door `setCertificateResponseCallback` API. U kunt instellen `setCertificateResponseCallback` om het standaardgedrag te overschrijven. Als u bijvoorbeeld een `certificateResponseType` die niet `ArrayBuffer`kunt u deze callback gebruiken om de certificaatreactie om te zetten in de `ArrayBuffer` type.

```js
var base64DecodeUint8Array = function (input) { 
        var raw = window.atob(input); 
        var rawLength = raw.length; 
        var array = new Uint8Array(new ArrayBuffer(rawLength)); 
 
        for (var i = 0; i < rawLength; i++) 
            array[i] = raw.charCodeAt(i); 
 
        return array; 
    }, 
  
onCertificateResponseCallback = function (certificateResponse) { 
    if(certificateResponse) { 
        var certText = certificateResponse.trim(); 
        certText = certText.replace(/^"(.+(?="$))"$/, '$1'); 
        return base64DecodeUint8Array(certText); 
    } 
}; 
  
drmManager.setCertificateResponseCallback(onCertificateResponseCallback);
```

<!--<a id="section_4DCC1B3ABCED484EB5340A558C9A770A"></a>-->

U kunt callback functies bepalen om het vergunningsbericht en de vergunningsreactie te ontleden en hen in een vraag over te gaan aan `drmManager.acquireLicense`. `onLicenseResponseCallback` is een nieuwe parameter in de `acquireLicense` API.

```js
var base64EncodeUint8Array = function (input) { 
        var keyStr = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/="; 
        var output = ""; 
        var chr1, chr2, chr3, enc1, enc2, enc3, enc4; 
        var i = 0; 
        while (i < input.length) { 
            chr1 = input[i++]; 
            chr2 = i < input.length ? input[i++] : Number.NaN; // Not sure if the index 
            chr3 = i < input.length ? input[i++] : Number.NaN; // checks are needed here 
  
            enc1 = chr1 >> 2; 
            enc2 = ((chr1 & 3) << 4) | (chr2 >> 4); 
            enc3 = ((chr2 & 15) << 2) | (chr3 >> 6); 
            enc4 = chr3 & 63; 
  
            if (isNaN(chr2)) { 
                enc3 = enc4 = 64; 
            } else if (isNaN(chr3)) { 
                enc4 = 64; 
            } 
            output += keyStr.charAt(enc1) + keyStr.charAt(enc2) + 
                keyStr.charAt(enc3) + keyStr.charAt(enc4); 
        } 
        return output; 
    }, 
  
    base64DecodeUint8Array = function (input) { 
        var raw = window.atob(input); 
        var rawLength = raw.length; 
        var array = new Uint8Array(new ArrayBuffer(rawLength)); 
  
        for (var i = 0; i < rawLength; i++) 
            array[i] = raw.charCodeAt(i); 
  
        return array; 
    }, 
  
    onLicenseMessageCallback = function (drmLicenseRequest) { 
        var licenseMessage = drmLicenseRequest.licenseMessage, 
            base64Message = base64EncodeUint8Array(licenseMessage); 
        return base64Message; 
    }, 
  
    onLicenseResponseCallback = function (serverResponse) { 
        var keyText = serverResponse.licenseResponse.trim(); 
        keyText = keyText.replace(/^"(.+(?="$))"$/, '$1'); 
        return base64DecodeUint8Array(keyText); 
    };

drmManager.acquireLicense(drmMetadata, null, acquireLicenseListener, onLicenseMessageCallback, onLicenseResponseCallback);
```

In de Gegevens van de Bescherming, nieuw **[!UICONTROL certificateResponseType]** wordt gebruikt om het type certificaatreactie in te stellen. Hier volgt een voorbeeld van beveiligingsgegevens:

```js
{ 
     "com.apple.fps.1_0": { 
         "serverURL": "https://fairplay.license.istreamplanet.com/api/license/9d3ed760-3ba9-4042-b4a4-07e0d8069200", 
         "certificateURL":"https://fairplay-stage.license.istreamplanet.com/api/AppCert/9d3ed760-3ba9-4042-b4a4-07e0d8069200", 
         "licenseResponseType": "text", 
         "certificateResponseType": "text", 
         "httpRequestHeaders": { 
            "Content-type": "application/x-www-form-urlencoded" 
         } 
     } 
}
```

Met de `certificateResponseType` veld is optioneel. Indien deze waarde niet wordt gebruikt, wordt ervan uitgegaan dat `ArrayBuffer`.
