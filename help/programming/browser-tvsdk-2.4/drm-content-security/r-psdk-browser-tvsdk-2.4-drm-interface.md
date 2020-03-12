---
description: Browser TVSDK biedt een DRM-interface waarmee u inhoud kunt afspelen die is beveiligd door verschillende DRM-oplossingen, zoals FairPlay, PlayReady en Widevine.
seo-description: Browser TVSDK biedt een DRM-interface waarmee u inhoud kunt afspelen die is beveiligd door verschillende DRM-oplossingen, zoals FairPlay, PlayReady en Widevine.
seo-title: Overzicht van de DRM-interface
title: Overzicht van de DRM-interface
uuid: b553ebad-8310-4517-8d97-ef8a1c5f4340
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Overzicht van de DRM-interface{#drm-interface-overview}

Browser TVSDK biedt een DRM-interface waarmee u inhoud kunt afspelen die is beveiligd door verschillende DRM-oplossingen, zoals FairPlay, PlayReady en Widevine.

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRM-ondersteuning is beschikbaar voor MPEG-Dash-streams die zijn beveiligd met Microsoft PlayReady (in Internet Explorer op Windows 8.1 en Edge) en Widevine (op Google Chrome) DRM-systemen. DRM-ondersteuning is beschikbaar voor HLS-streams in Safari die zijn beveiligd met FairPlay.

De belangrijkste interface van de DRM-workflow is de `DRMManager`. Een verwijzing naar de `DRMManager` instantie kan via de instantie MediaPlayer worden verkregen:

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

Hier volgt een workflow op hoog niveau voor het afspelen van DRM-beveiligde inhoud:

1. Om de DRM-systeem-specifieke gegevens vast te maken die door Browser TVSDK in het proces van de vergunningsverwerving voor een beschermde stroom zullen worden gebruikt, maak de volgende vraag alvorens `mediaPlayer.replaceCurrentResource`:

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
          "serverURL": { 
             "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
             "license-request": "https://example.com:8096/flashaccess/req", 
             "license-release": "https://example.com:8096/flashaccess/req" 
          }, 
          "httpRequestHeaders": { 
          } 
       } 
   }; 
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. Als wordt verwacht dat dezelfde inhoud in verschillende browsers met verschillende DRM-systemen werkt, kunnen voor meerdere DRM-systemen beveiligingsgegevens worden opgegeven.

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
           "serverURL": { 
               "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
               "license-request": "https://example.com:8096/flashaccess/req", 
               "license-release": "https://example.com:8096/flashaccess/req" 
           }, 
           "httpRequestHeaders": { 
           } 
       }, 
       "com.widevine.alpha": { 
           "serverURL": "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "dt-custom-data": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.microsoft.playready": { 
           "serverURL": "https://pr.test.expressplay.com/playready/RightsManager.asmx?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "http-header-CustomData": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.apple.fps.1_0": { 
           "serverURL": "https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<token value>", 
           "certificateURL": "Path_To_certificate.cer", 
           "licenseResponseType": "arraybuffer", 
           "httpRequestHeaders": { 
               "Content-type": "application/octet-stream" 
           } 
       }, 
       "org.w3.clearkey": { 
           "clearkeys": { 
               "H3JbV93QV3mPNBKQON2UtQ": "ClKhDPHMtCouEx1vLGsJsA", 
               "IAAAACAAIAAgACAAAAAAAg": "5t1CjnbMFURBou087OSj2w" 
           } 
       } 
   }; 
   
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. Wanneer geen beveiligingsgegevens zijn ingesteld, wordt de benodigde informatie, zoals de licentie-URL, indien van toepassing opgehaald uit het vak PSSH voor DRM-systemen.

   >[!TIP]
   >
   >Als u beveiligingsgegevens opgeeft, wordt de licentie-URL die in het vak PSSH is opgegeven, overschreven.

1. Standaard is het sessietype voor de DRM-licentie tijdelijk, wat betekent dat de licentie niet wordt opgeslagen nadat de sessie is gesloten.

   U kunt een sessietype opgeven met behulp van een API in `DRMManager`.  Voor achterwaartse verenigbaarheid, omvatten de zittingstypes `temporary`, `persistent-license`, `persistent-usage-record`, en `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. Wanneer het `sessionType` gebruikte is `persistent-license` of `persistent`, kan de vergunning DRM door het aanhalen worden teruggekeerd `DRMManager.returnLicense`.

   ```js
   var onLicenseReturnFunc = function () { 
       console.log("DRM: License Return Complete "); 
   }, 
   
   onLicenseReturnErrorFunc = function (major, minor, errorString/*, errorServerUrl*/) { 
      console.log("DRM: License Return Error: " + errorString); 
   }, 
   
   drmManager = mediaPlayer.drmManager; 
   
   if (drmManager) { 
       var returnLicenseListener = new  
           AdobePSDK.DRMReturnLicenseListener(onLicenseReturnFunc, onLicenseReturnErrorFunc); 
       drmManager.returnLicense(null, null, null, false, returnLicenseListener, drmLicense.session); 
   }
   ```

