---
description: Als u FairPlay Streaming wilt implementeren in uw TVSDK-app, moet u een Resource Loader schrijven die een aanvraag voor het aanschaffen van licenties naar uw FairPlay Streaming-server verzendt.
seo-description: Als u FairPlay Streaming wilt implementeren in uw TVSDK-app, moet u een Resource Loader schrijven die een aanvraag voor het aanschaffen van licenties naar uw FairPlay Streaming-server verzendt.
seo-title: Apple FairPlay in TVSDK-toepassingen
title: Apple FairPlay in TVSDK-toepassingen
uuid: 4384d379-37cd-46c5-8c25-0cda16bdebb8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---


# Apple FairPlay in TVSDK-toepassingen {#apple-fairplay-in-tvsdk-applications}

Als u FairPlay Streaming wilt implementeren in uw TVSDK-app, moet u een Resource Loader schrijven die een aanvraag voor het aanschaffen van licenties naar uw FairPlay Streaming-server verzendt.

De code van de Loader van het Middel is verantwoordelijk voor de volgende taken:

1. Bepaal waar u het verzoek tot verwerving van een licentie wilt verzenden.
1. Maak de aanvraag op.
1. Geef de benodigde informatie op aan de server, zodat de server kan beslissen of het verzoek is toegestaan.

Als u bijvoorbeeld Adobe Primetime Cloud DRM gebruikt met ExpressPlay, verzendt de Resource Loader de aanvraag naar:

```
https://fp-gen.service.expressplay.com
```

De Resource Loader maakt de aanvraag op en voegt een ExpressPlay-token toe dat het afspelen naar de URL toestaat. Wanneer het verwerven van het token ExpressPlay moet u rekening houden met verschillende opties. Deze opties worden bepaald door de manier waarop u de inhoud hebt verpakt.

Wanneer u de inhoud verpakt, voegt de pakketsoftware `skd:` URL&#39;s in uw M3U8-manifest in. Na de `skd:` ingang, kunt u om het even welke gegevens in manifest zetten. U kunt deze gegevens in uw toepassingscode gebruiken om de hierboven vermelde taken te voltooien. U kunt bijvoorbeeld `skd:{content_id}` gebruiken, zodat uw toepassing de id kan bepalen van de inhoud die wordt afgespeeld en een token kan aanvragen voor die specifieke inhoud. U kunt bijvoorbeeld ook `skd:{entitlement_server_url}?cid={content_id}` gebruiken, zodat de URL van de machtigingsserver niet hoeft te zijn gecodeerd.

U hebt mogelijk geen informatie in uw `skd:` URL nodig als u, wanneer het afspelen begint, de inhoud-id al via andere kanalen kent. Het tweede voorbeeld is een ideale oplossing om uw opstelling te testen, maar u kunt het ook in een productiemilieu gebruiken.

>[!TIP]
>
>U bepaalt de indeling van `skd:`.

Uw inhoud wordt verkregen door het `skd:` protocol te gebruiken, maar uw vergunningsverzoek gebruikt `https:`. De gemeenschappelijkste opties om deze protocollen te behandelen zijn:

* **Eerste tests van end-to-end** afspelenSelecteer een  `skd:` URL wanneer u de inhoud verpakt. Wanneer u uw app test, moet u handmatig een licentie aanschaffen bij ExpressPlay en de licentie- (een `https:` URL) en inhoud-URL in uw lader coderen.

   Bijvoorbeeld:

   ```
   NSString* const PLAYLIST_URL =  
     @"https://{your_content_URL}/{your_manifest}.m3u8"; 
   NSString* const EXPRESSPLAY_TOKEN =  
     @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
       ExpressPlayToken={copy_your_token_to_here}";
   ```

* **De meeste andere** gevallenWanneer u de inhoud verpakt, selecteert u een  `skd:` URL die uniek de id van de inhoud vertegenwoordigt. Analyseer de URL `skd:` in de lader, stuur deze naar de server om een token aan te schaffen en gebruik de resulterende token als URL.

   Bijvoorbeeld:

   ```
   - (BOOL)resourceLoader:(AVAssetResourceLoader *)resourceLoader  
         shouldWaitForLoadingOfRequestedResource:(AVAssetResourceLoadingRequest *)loadingRequest { 
       NSURL *url = [[loadingRequest request] URL]; 
       if (![[url scheme] isEqual:@"skd"]) 
           return NO; 
   
       NSString *strUrl = [url absoluteString]; 
       NSLog(@"url is: %@", strUrl); 
   
       strUrl = [strUrl stringByReplacingOccurrencesOfString:@"skd://" withString:@"https://"]; 
   
       NSData *assetId; 
   
       NSData *requestBytes; 
       NSError* error = nil; 
       BOOL handled = NO; 
   
       NSData  *responseData = nil; 
   
       assetId = getMyAssetIdentifierFromURL(url); 
   
       /* Usecase 1: "On Premise Fairplay Server" 
        * Set the strUrl to the OnPremise Fairplay Server Url. The OnPremise Fairplay  
        * Server Url is either hardcoded in the App or derived from strUrl. 
        */ 
   #if 0  
       // Insert your use case 1 codes here: 
       // strUrl = getOnPremiseServerUrl(strUrl, assetId); 
   #endif // 
   
       /* Usecase 2: The strUrl is the entitlement server. 
        * Send assetId to the entitlement server; if the user is allowed to playback  
        * the content, the entitlement server will send back an ExpressPlay Token Url. 
        */ 
   
   #if 0 
       // The hardcoded SEES server: 
       strUrl = @"https://10.0.248.85:8080/sees/SEESServlet"; 
   
       // You can use the following code to simulate a device binding entitlement  
       // request:  
       // First, invoke getExpressPlayTokenUrlFromEntilementServer with  
       // bEnforceDeviceID set to false. When you play the content, the device_id  
       // will be registered on the ExpressPlay Server.  Now change code to set  
       // bEnforceDeviceID to true, and rerun the program. The ExpressPlay token  
       // sent back by the SEES server will be device bound. 
   
       // The strUrl returned below is the ExpressPlay Token URL. 
       strUrl = getExpressPlayTokenUrlFromEntilementServer(strUrl, assetId, true, &error); 
   #endif 
   
       /* Usecase 3: The strUrl is already the ExpressPlay Token Url. 
        */ 
   
       // Read in the certificate 
       NSLog(@"Get Application Certificate"); 
       NSString* certPath = [[NSBundle mainBundle] pathForResource:@"my_certificate.cer"  
                                                            ofType:nil]; 
   
       NSData *appCert = [NSData dataWithContentsOfFile:certPath]; 
   
       // To create the request blob for the server: 
       requestBytes = [loadingRequest streamingContentKeyRequestDataForApp: appCert 
                                                         contentIdentifier:assetId  
                                                                   options:nil  
                                                                     error:&error]; 
       if (requestBytes == nil) { 
           NSLog(@"Error creating server request: %@", error); 
           return false; 
       } 
       // Per the specification, send requestBytes along with the assetId to the Key 
       // Server and obtain the response. 
       NSError *err; 
   
       responseData = getCKCFromExpressPlayService( strUrl, requestBytes, assetId, &err); 
   
       if (responseData != nil) { 
           NSLog(@"Get response data: "); 
           [loadingRequest finishLoadingWithResponse:nil  
                                                data:(NSData *)responseData 
                                            redirect:nil]; 
       } 
       else { 
           [loadingRequest finishLoadingWithError:err]; 
           NSLog(@"bad key response"); 
       } 
       handled = YES; 
   bail: 
       return handled; 
   
   }
   ```

## Apple FairPlay inschakelen in TVSDK-toepassingen{#enable-apple-fairplay-in-tvsdk-applications}

U kunt Apple FairPlay Streaming, de DRM-oplossing van Apple, implementeren in uw TVSDK-toepassingen.

1. Maak uw FairPlay-lader voor klantbronnen door `PTAVAssetResourceLoaderDelegate` te implementeren.

   Zie [Apple FairPlay in TVSDK-toepassingen](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md) voor meer informatie.

   >[!NOTE]
   >
   >Zorg ervoor dat u de instructies opvolgt in de *FairPlay Streaming Program Guide* ( *FairPlayStreaming_PG.pdf*), die is opgenomen in [FairPlay Server SDK voor het ontwikkelen van een FPS-compatibele app](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   De `resourceLoader:shouldWaitForLoadingOfRequestedResource` methode is gelijkwaardig aan wat in `AVAssetResourceLoaderDelegate` is.

   >[!IMPORTANT]
   >
   >Als u inhoud wilt afspelen in het ExpressPlay-licentieserverscenario, wijzigt u het URL-schema in uw ExpressPlay FairPlay-serverlicentieaanvraag-URL van `skd://` in `https://` (of `https://`).

1. Registreer de *FairPlay* Loader voor hulpbronnen van klanten met `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Als u uw eigen FairPlay-licentieserver hebt geschreven of als u een externe FairPlay-licentieserver gebruikt, neemt u contact op met de leverancier van de licentieserver om de URL, opmaak en andere vereisten voor uw licentieserver te bepalen.