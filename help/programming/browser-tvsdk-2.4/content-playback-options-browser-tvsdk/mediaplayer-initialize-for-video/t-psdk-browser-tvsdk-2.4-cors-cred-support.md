---
description: De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
seo-description: De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.
seo-title: Bron delen tussen verschillende oorsprong
title: Bron delen tussen verschillende oorsprong
uuid: e788b542-d4ac-48aa-91e2-1e88068cbba1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Bron delen tussen verschillende oorsprong {#cross-origin-resource-sharing}

De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.

Wanneer de cliënt om manifest, segment, of sleutel verzoekt, kan de server een koekje plaatsen dat de cliënt voor verdere verzoeken moet overgaan. Om het lezen en schrijven van cookies mogelijk te maken, moet de client het `withCredentials` kenmerk instellen op `true` voor aanvragen van een andere oorsprong.

Om `withCredentials` steun voor de meeste soorten verzoeken toe te laten wanneer het spelen van een bepaalde media middel:

1. Maak het `CORSConfig` object.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Koppel het object `corsConfig` aan het `NetworkConfiguration` object en stel het in `useCookieHeaderForAllRequests` op `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Instellen `networkConfig` in het `MediaPlayerItemConfig` object.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Geef `MediaPlayerItemConfig` de `MediaPlayer.replaceCurrentResource` methode door.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>De `useCookieHeaderForAllRequests` markering heeft geen invloed op vergunningaanvragen. Als u het `withCredentials` kenmerk wilt instellen op `true` voor een licentieaanvraag, moet u het `withCredentials` kenmerk in uw beveiligingsgegevens instellen of een machtigingssleutel opgeven in de `httpRequestHeaders` beveiligingsgegevens. Bijvoorbeeld:

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

De vlag beïnvloedt geen vergunningsverzoek omdat sommige servers het `Access-Control-Allow-Origin` gebied aan vervanging (&#39;*&#39;) in hun reactie plaatsen. Maar wanneer de geloofsbrieven vlag aan wordt geplaatst, kan het vervangingsniet binnen worden gebruikt `true``Access-Control-Allow-Origin`. Als u instelt `useCookieHeaderForAllRequests` op `true` voor alle typen aanvragen, wordt mogelijk de volgende fout weergegeven voor een licentieaanvraag:

De volgende informatie onthouden:

* Wanneer een vraag met `withCredentials=true` ontbreekt, Browser TVSDK probeert de vraag zonder `withCredentials`.
* Wanneer een vraag met wordt gemaakt `networkConfiguration.useCookieHeaderForAllRequests=false`, worden de verzoeken XHR gemaakt zonder de `withCredentials` attributen.