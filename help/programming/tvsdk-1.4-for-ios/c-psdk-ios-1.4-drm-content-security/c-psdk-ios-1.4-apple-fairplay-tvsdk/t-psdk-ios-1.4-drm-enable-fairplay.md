---
description: U kunt Apple FairPlay Streaming, een Apple DRM-oplossing, implementeren in uw TVSDK-toepassingen.
title: Apple FairPlay inschakelen in TVSDK-toepassingen
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Apple FairPlay inschakelen in TVSDK-toepassingen{#enable-apple-fairplay-in-tvsdk-applications}

U kunt Apple FairPlay Streaming, een Apple DRM-oplossing, implementeren in uw TVSDK-toepassingen.

1. Maak uw FairPlay Customer Resource Loader door deze te implementeren `PTAVAssetResourceLoaderDelegate`.

   Zie voor meer informatie [Apple FairPlay in TVSDK-toepassingen](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md).

   >[!NOTE]
   >
   >Zorg ervoor dat u de instructies in de *FairPlay Streaming Program Guide* ( *FairPlayStreaming_PG.pdf*), die is opgenomen in [FairPlay Server SDK voor het ontwikkelen van een FPS-compatibele app](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   De `resourceLoader:shouldWaitForLoadingOfRequestedResource` methode is gelijk aan wat zich bevindt in `AVAssetResourceLoaderDelegate`.

   >[!IMPORTANT]
   >
   >Als u inhoud wilt afspelen in het ExpressPlay-licentieserverscenario, wijzigt u het URL-schema in uw ExpressPlay FairPlay-serverlicentieaanvraag voor de URL van `skd://` tot `https://` (of `https://`).

1. Registreer de *FairPlay* Bron van klant Loader met `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Als u uw eigen FairPlay-licentieserver hebt geschreven of als u een externe FairPlay-licentieserver gebruikt, neemt u contact op met de leverancier van de licentieserver om de URL, opmaak en andere vereisten voor uw licentieserver te bepalen.
