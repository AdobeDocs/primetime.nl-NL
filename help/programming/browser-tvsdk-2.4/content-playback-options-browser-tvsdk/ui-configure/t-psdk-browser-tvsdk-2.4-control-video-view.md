---
description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
seo-description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
seo-title: De positie en grootte van de videoweergave bepalen
title: De positie en grootte van de videoweergave bepalen
uuid: d09dbc18-1ec0-4336-bf3f-7ff6c265c443
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# De positie en grootte van de videoweergave bepalen{#control-the-position-and-size-of-the-video-view}

U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.

Browser TVSDK door gebrek probeert om de aspectverhouding van de videomening te handhaven wanneer de grootte of de positie van de video wegens een verandering door de toepassing, een profielschakelaar, een inhoudschakelaar, etc. verandert.

U kunt het standaardgedrag voor de verhouding overschrijven door een ander *schaalbeleid* op te geven. Geef het schaalbeleid op met de `MediaPlayerView` eigenschap van het `scalePolicy` object. Het standaardschaalbeleid van `MediaPlayerView` wordt ingesteld met een instantie van de `MaintainAspectRatioScalePolicy` klasse. Als u het schaalbeleid opnieuw wilt instellen, vervangt u de standaardinstantie van `MaintainAspectRatioScalePolicy` Aan `MediaPlayerView.scalePolicy` door uw eigen beleid.

>[!IMPORTANT]
>
>U kunt de `scalePolicy` eigenschap niet instellen op een null-waarde.

## Niet-Flash fallback-scenario&#39;s {#non-flash-fallback-scenarios}

In niet-Flash-fallbackscenario&#39;s zou het div-element van de video in de `View` constructor voor een juist schaalbeleid andere waarden dan nul moeten retourneren voor `offsetWidth` en `offsetHeight`. Als u een voorbeeld wilt geven van een onjuiste functie, kan het gebeuren dat wanneer de breedte en hoogte van de div-elementen van de video niet expliciet in css zijn ingesteld, de `View` constructor nul retourneert voor `offsetWidth` of `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy biedt beperkte ondersteuning voor een aantal browsers, met name IE, Edge en Safari 9. Voor deze browsers kan de native hoogte-breedteverhouding van de video niet worden gewijzigd. De positie en afmetingen van de video worden echter afgedwongen volgens het schaalbeleid.

1. Implementeer de `MediaPlayerViewScalePolicy` interface om uw eigen schaalbeleid te maken.

   De methode `MediaPlayerViewScalePolicy` heeft één methode:

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

1. Wijs uw implementatie toe aan de `MediaPlayerView` eigenschap.

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. Voeg uw mening aan het `view` bezit van Media Player toe.

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**Bijvoorbeeld: Schaal de video om de volledige videomening te vullen, zonder aspectverhouding te handhaven:**

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

