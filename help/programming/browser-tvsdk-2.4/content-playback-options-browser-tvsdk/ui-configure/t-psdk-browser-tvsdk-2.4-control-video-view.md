---
description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
seo-description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
seo-title: De positie en grootte van de videoweergave bepalen
title: De positie en grootte van de videoweergave bepalen
uuid: d09dbc18-1ec0-4336-bf3f-7ff6c265c443
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---


# De positie en grootte van de videoweergave bepalen{#control-the-position-and-size-of-the-video-view}

U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.

Browser TVSDK door gebrek probeert om de aspectverhouding van de videomening te handhaven wanneer de grootte of de positie van de video wegens een verandering door de toepassing, een profielschakelaar, een inhoudschakelaar, etc. verandert.

U kunt het standaardgedrag van de aspectverhouding met voeten treden door een verschillend *schaalbeleid* te specificeren. Geef het schaalbeleid op met de eigenschap `MediaPlayerView` van het object. `scalePolicy` Het standaardschaalbeleid van `MediaPlayerView` wordt geplaatst met een geval van de `MaintainAspectRatioScalePolicy` klasse. Om het schaalbeleid terug te stellen, vervang de standaardinstantie van `MaintainAspectRatioScalePolicy` op `MediaPlayerView.scalePolicy` met uw eigen beleid.

>[!IMPORTANT]
>
>U kunt de eigenschap `scalePolicy` niet instellen op een null-waarde.

## Niet-Flash fallbackscenario&#39;s {#non-flash-fallback-scenarios}

In niet-Flash fallback scenario&#39;s, voor schaalbeleid om correct te werken, zou het video div element dat in de `View` aannemer wordt gegeven niet-nul waarden voor `offsetWidth` en `offsetHeight` moeten terugkeren. Als u een voorbeeld van een onjuiste functie wilt weergeven, soms wanneer de breedte en hoogte van de div-elementen van de video niet expliciet zijn ingesteld in css, retourneert de constructor `View` nul voor `offsetWidth` of `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy biedt beperkte ondersteuning voor een aantal browsers, met name IE, Edge en Safari 9. Voor deze browsers kan de native hoogte-breedteverhouding van de video niet worden gewijzigd. De positie en afmetingen van de video worden echter afgedwongen volgens het schaalbeleid.

1. Implementeer de interface `MediaPlayerViewScalePolicy` om uw eigen schaalbeleid te maken.

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

1. Wijs uw implementatie aan het `MediaPlayerView` bezit toe.

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

