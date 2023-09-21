---
description: De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.
keywords: CORS;cross origin;resource sharing;cookies;withCredentials
title: Bron delen tussen verschillende oorsprong
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Bron delen tussen verschillende oorsprong {#cross-origin-resource-sharing}

De steun voor het attribuut withCredentials in XMLHttpRequests staat het delen van middelen van oorsprong (CORS) verzoeken toe om de koekjes van het doeldomein voor een verscheidenheid van verzoektypes te omvatten.

Wanneer de cliënt om manifest, segment, of sleutel verzoekt, kan de server een koekje plaatsen dat de cliënt voor verdere verzoeken moet overgaan. Om het lezen en schrijven van cookies mogelijk te maken, moet de client de instelling `withCredentials` kenmerk naar `true` voor verzoeken om wederkerige oorsprong.

Inschakelen `withCredentials` ondersteuning voor de meeste typen verzoeken bij het afspelen van een bepaalde mediabronis:

1. Maak de `CORSConfig` object.

   ```js
   var corsConfig = new AdobePSDK.CORSConfig();  
   corsConfig.enableEncryptionRequest = true; 
   ```

1. Koppel de `corsConfig` aan de `NetworkConfiguration` object en set `useCookieHeaderForAllRequests` tot `true`.

   ```js
   var networkConfig = new AdobePSDK.NetworkConfiguration();  
   networkConfig.CORSConfig = corsConfig; 
   networkConfiguration.useCookieHeaderForAllRequests= true;
   ```

1. Set `networkConfig` in de `MediaPlayerItemConfig` object.

   ```js
   var mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig();  
   mediaPlayerItemConfig.networkConfiguration = networkConfig; 
   ```

1. Voldoende `MediaPlayerItemConfig` aan de `MediaPlayer.replaceCurrentResource` methode.

   ```js
   var player = new AdobePSDK.MediaPlayer(); 
   mediaResource = new AdobePSDK.MediaResource(url, AdobePSDK.MediaResourceType.HLS);  
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);  
   ```

>[!IMPORTANT]
>
>De `useCookieHeaderForAllRequests` de markering heeft geen invloed op vergunningaanvragen. Als u het dialoogvenster `withCredentials` kenmerk naar `true` voor een licentieaanvraag moet u de instelling `withCredentials` in uw beveiligingsgegevens of geef een machtigingssleutel op in het veld `httpRequestHeaders` van uw beveiligingsgegevens. Bijvoorbeeld:

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

De vlag beïnvloedt geen vergunningsverzoek omdat sommige servers plaatsen `Access-Control-Allow-Origin` veld naar jokerteken (&#39;&#42;&quot;) in hun antwoord. Maar, wanneer de geloofsbrieven vlag wordt geplaatst aan `true`, kan het jokerteken niet worden gebruikt in `Access-Control-Allow-Origin`. Als u `useCookieHeaderForAllRequests` tot `true` voor alle soorten verzoeken, zou u de volgende fout voor een vergunningsverzoek kunnen zien:

De volgende informatie onthouden:

* Wanneer een vraag met `withCredentials=true` ontbreekt, Browser TVSDK probeert opnieuw de vraag zonder `withCredentials`.
* Wanneer een vraag met wordt gemaakt `networkConfiguration.useCookieHeaderForAllRequests=false`, XHR-verzoeken worden ingediend zonder de `withCredentials` kenmerk.
