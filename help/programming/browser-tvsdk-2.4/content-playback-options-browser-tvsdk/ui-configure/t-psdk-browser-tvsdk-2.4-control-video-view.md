---
description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
title: De positie en grootte van de videoweergave bepalen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# De positie en grootte van de videoweergave bepalen{#control-the-position-and-size-of-the-video-view}

U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.

Browser TVSDK door gebrek probeert om de aspectverhouding van de videomening te handhaven wanneer de grootte of de positie van de video wegens een verandering door de toepassing, een profielschakelaar, een inhoudschakelaar, etc. verandert.

U kunt het standaardgedrag voor de verhouding overschrijven door een andere waarde op te geven *schaalbeleid*. Geef het schaalbeleid op met de opdracht `MediaPlayerView` object `scalePolicy` eigenschap. Het standaardschaalbeleid van `MediaPlayerView` wordt ingesteld met een instantie van de `MaintainAspectRatioScalePolicy` klasse. Vervang de standaardinstantie van `MaintainAspectRatioScalePolicy` op `MediaPlayerView.scalePolicy` met uw eigen beleid.

>[!IMPORTANT]
>
>U kunt de instelling `scalePolicy` aan een null-waarde.

## Fallback-scenario&#39;s zonder Flash {#non-flash-fallback-scenarios}

In niet-Flash fallback scenario&#39;s, voor schaalbeleid om correct te werken, het video div element dat in wordt gegeven `View` constructor moet andere waarden dan nul retourneren voor `offsetWidth` en `offsetHeight`. Als u een voorbeeld wilt geven van een onjuiste functie, kan het gebeuren dat wanneer de breedte en hoogte van de div-elementen van de video niet expliciet zijn ingesteld in css, de instelling `View` constructor retourneert nul voor `offsetWidth` of `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy biedt beperkte ondersteuning voor een aantal browsers, met name IE, Edge en Safari 9. Voor deze browsers kan de native hoogte-breedteverhouding van de video niet worden gewijzigd. De positie en afmetingen van de video worden echter afgedwongen volgens het schaalbeleid.

1. Implementeer de `MediaPlayerViewScalePolicy` om uw eigen schaalbeleid te maken.

   De `MediaPlayerViewScalePolicy` heeft één methode:

   ```js
   /** 
   * Adjust the specified rectangle to match the new video dimensions. 
   * @param viewPort {AdobePSDK.Rectangle}The video rectangle as absolute position. 
   * @param videoWidth {Number}The video width. 
   * @param videoHeight {Number} The video height. 
   * @return {AdobePSDK.Rectangle} an adjusted rectangle. 
   */ 
   function adjustCallbackFunc(viewPort, videoWidth, videoHeight);
   ```

   Bijvoorbeeld:

   ```js
   /** 
   Default Constructor 
   */ 
   MediaPlayerViewCustomScalePolicy = function() { 
       return this; 
   }; 
   MediaPlayerViewCustomScalePolicy.prototype = { 
       constructor: MediaPlayerViewScalePolicy, 
       adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
           /* Your Custom Adjustment here. */ 
           [...] 
           return adjustedRectangle; 
       } 
   };
   ```

1. Uw implementatie toewijzen aan de `MediaPlayerView` eigenschap.

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. Uw weergave toevoegen aan de mediaspeler `view` eigenschap.

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Bijvoorbeeld: schaal de video om de volledige videoweergave te vullen, zonder de hoogte-breedteverhouding te behouden:**

```
/** 
 * Default constructor. 
 */ 
MediaPlayerViewCustomScalePolicy = function() { 
    return this; 
}; 
MediaPlayerViewCustomScalePolicy.prototype = { 
    constructor: MediaPlayerViewScalePolicy, 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
        return viewPort; 
    } 
}; 
var view = new AdobePSDK.MediaPlayerView(videoDiv); 
view.scalePolicy = new MediaPlayerViewCustomScalePolicy (); 
mediaPlayer.view = view;
```
