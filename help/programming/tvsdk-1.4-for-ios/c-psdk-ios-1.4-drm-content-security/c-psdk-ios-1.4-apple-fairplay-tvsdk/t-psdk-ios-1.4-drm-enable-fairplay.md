---
description: U kunt Apple FairPlay Streaming, de DRM-oplossing van Apple, implementeren in uw TVSDK-toepassingen.
seo-description: U kunt Apple FairPlay Streaming, de DRM-oplossing van Apple, implementeren in uw TVSDK-toepassingen.
seo-title: Apple FairPlay inschakelen in TVSDK-toepassingen
title: Apple FairPlay inschakelen in TVSDK-toepassingen
uuid: fafffdb9-09f9-45fb-9957-3c6e95ed55f9
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Apple FairPlay inschakelen in TVSDK-toepassingen{#enable-apple-fairplay-in-tvsdk-applications}

U kunt Apple FairPlay Streaming, de DRM-oplossing van Apple, implementeren in uw TVSDK-toepassingen.

1. Maak uw FairPlay-lader voor klantbronnen door deze te implementeren `PTAVAssetResourceLoaderDelegate`.

   Zie [Apple FairPlay in TVSDK-toepassingen](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)voor meer informatie.

   >[!NOTE]
   >
   >Zorg ervoor dat u de instructies opvolgt in de *FairPlay Streaming Program Guide* ( *FairPlayStreaming_PG.pdf*), die is opgenomen in de SDK van [FairPlay Server voor het ontwikkelen van een FPS-compatibele app](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)).

   De `resourceLoader:shouldWaitForLoadingOfRequestedResource` methode is gelijk aan de methode `AVAssetResourceLoaderDelegate`in.

   >[!IMPORTANT] {Important=&quot;high&quot;}
   >
   >Als u inhoud wilt afspelen in het ExpressPlay-licentieserverscenario, wijzigt u het URL-schema in uw ExpressPlay FairPlay-serverlicentieaanvraag-URL van `skd://` naar `https://` (of `https://`).

1. Registreer de *FairPlay* Customer Resource Loader bij `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

Als u uw eigen FairPlay-licentieserver hebt geschreven of als u een externe FairPlay-licentieserver gebruikt, neemt u contact op met de leverancier van de licentieserver om de URL, opmaak en andere vereisten voor uw licentieserver te bepalen.
