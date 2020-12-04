---
description: De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.
seo-title: Bron delen tussen verschillende oorsprong
title: Bron delen tussen verschillende oorsprong
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Bronnen delen tussen verschillende oorsprong {#cross-origin-resource-sharing}

De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.

Wanneer de cliënt om manifest, segment, of sleutel verzoekt, kan de server een koekje plaatsen dat de cliënt voor verdere verzoeken moet overgaan. Om het lezen en schrijven van cookies mogelijk te maken, moet de client het `withCredentials`-kenmerk instellen op `true` voor aanvragen van een andere oorsprong.

Om `withCredentials` steun voor de meeste soorten verzoeken toe te laten wanneer het spelen van een bepaalde media middel:

1. Maak het object `CORSConfig`.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Koppel `corsConfig` aan het `NetworkConfiguration`-object en stel `useCookieHeaderForAllRequests` in op `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Stel `networkConfig` in het object `MediaPlayerItemConfig` in.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Geef `MediaPlayerItemConfig` door aan de `MediaPlayer.replaceCurrentResource` methode.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>De markering `useCookieHeaderForAllRequests` heeft geen invloed op licentieaanvragen. Als u het `withCredentials`-kenmerk wilt instellen op `true` voor een licentieaanvraag, moet u het `withCredentials`-kenmerk in uw beveiligingsgegevens instellen of een machtigingssleutel opgeven in `httpRequestHeaders` van uw beveiligingsgegevens. Bijvoorbeeld:

```
# Example 1 
{ 
    "com.widevine.alpha": {  
        "withCredentials":true,  
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i]" } 
} 
 
# Example 2 
{ 
    "com.widevine.alpha": { 
        "httpRequestHeaders": {  
            "authorization": "true"  
            }, 
        "serverURL":  
          "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=[YOUR_TOKEN</i>]" }
        } 
}
```

De vlag beïnvloedt geen vergunningsverzoek omdat sommige servers `Access-Control-Allow-Origin` gebied aan vervanging (&#39;*&#39;) in hun reactie plaatsen. Maar wanneer de geloofsbrieven vlag aan `true` wordt geplaatst, kan het vervangingsniet in `Access-Control-Allow-Origin` worden gebruikt. Als u `useCookieHeaderForAllRequests` aan `true` voor alle soorten verzoeken plaatst, zou u de volgende fout voor een vergunningsverzoek kunnen zien:

De volgende informatie onthouden:

* Wanneer een vraag met `withCredentials=true` ontbreekt, Browser TVSDK probeert de vraag zonder `withCredentials` opnieuw.
* Wanneer een vraag met `networkConfiguration.useCookieHeaderForAllRequests=false` wordt gemaakt, worden de verzoeken XHR gemaakt zonder het `withCredentials` attribuut.