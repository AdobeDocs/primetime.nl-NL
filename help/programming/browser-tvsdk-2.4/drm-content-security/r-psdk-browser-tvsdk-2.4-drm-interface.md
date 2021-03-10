---
description: Browser TVSDK biedt een DRM-interface waarmee u inhoud kunt afspelen die is beveiligd door verschillende DRM-oplossingen, zoals FairPlay, PlayReady en Widevine.
title: Overzicht van de DRM-interface
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Overzicht van DRM-interface{#drm-interface-overview}

Browser TVSDK biedt een DRM-interface waarmee u inhoud kunt afspelen die is beveiligd door verschillende DRM-oplossingen, zoals FairPlay, PlayReady en Widevine.

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRM-ondersteuning is beschikbaar voor MPEG-Dash-streams die zijn beveiligd met Microsoft PlayReady (in Internet Explorer op Windows 8.1 en Edge) en Widevine (op Google Chrome) DRM-systemen. DRM-ondersteuning is beschikbaar voor HLS-streams in Safari die zijn beveiligd met FairPlay.

De belangrijkste interface van het DRM werkschema is `DRMManager`. Een verwijzing naar de instantie `DRMManager` kan via de instantie MediaPlayer worden verkregen:

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

Hier volgt een workflow op hoog niveau voor het afspelen van DRM-beveiligde inhoud:

1. Als u de DRM-systeemspecifieke gegevens wilt bijvoegen die door Browser TVSDK worden gebruikt in het licentieaanschafproces voor een beveiligde stream, roept u `mediaPlayer.replaceCurrentResource` als volgt aan:

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

   U kunt een sessietype opgeven met behulp van een API in `DRMManager`.  Voor achterwaartse verenigbaarheid, zittingstypes omvatten `temporary`, `persistent-license`, `persistent-usage-record`, en `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. Wanneer `sessionType` wordt gebruikt `persistent-license` of `persistent` is, kan de DRM vergunning worden teruggekeerd door &lt;a3 aan te halen/>.`DRMManager.returnLicense`

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

