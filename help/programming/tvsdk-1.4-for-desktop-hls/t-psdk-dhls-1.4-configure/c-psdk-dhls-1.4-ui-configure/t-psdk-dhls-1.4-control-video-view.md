---
description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
seo-description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
seo-title: De positie en grootte van de videoweergave bepalen
title: De positie en grootte van de videoweergave bepalen
uuid: 2231c574-03cd-45a8-ab00-4a42f8e044f0
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# De positie en grootte van de videoweergave bepalen{#control-the-position-and-size-of-the-video-view}

U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.

TVSDK probeert standaard de hoogte-breedteverhouding van de videoweergave te behouden wanneer de grootte of de positie van de video verandert (als gevolg van een wijziging die door de toepassing, een profielschakelaar of een inhoudsschakelaar is aangebracht, enz.).

U kunt het standaardgedrag voor de verhouding overschrijven door een ander *schaalbeleid* op te geven. Geef het schaalbeleid op met de `MediaPlayerView` eigenschap van het `scalePolicy` object. Het standaardschaalbeleid `MediaPlayerView`van de klasse wordt ingesteld met een instantie van de `MaintainAspectRatioScalePolicy` klasse. Als u het schaalbeleid opnieuw wilt instellen, vervangt u de standaardinstantie van `MaintainAspectRatioScalePolicy` Aan `MediaPlayerView.scalePolicy` door uw eigen beleid. (U kunt de `scalePolicy` eigenschap niet instellen op een null-waarde.)

1. Implementeer de `MediaPlayerViewScalePolicy` interface om uw eigen schaalbeleid te maken.

   De methode `MediaPlayerViewScalePolicy` heeft één methode:

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK gebruikt een `StageVideo` object voor de weergave van de video en omdat `StageVideo` objecten zich niet in het weergaveoverzicht bevinden, bevat de `viewPort` parameter de absolute coördinaten van de video.
   >
   >
   >Bijvoorbeeld:
   >
   >```
   >public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
   >       /** 
   >         * Default constructor. 
   >         */ 
   >       public function CustomScalePolicy() { 
   >       } 
   > 
   >    
      public function adjust(viewPort:Rectangle,  
   >                                                     videoWidth:Number,  
   >                                                     videoHeight:Number):Rectangle { 
   >               return customAdjustment(); 
   >       } 
   > 
   >    
      public function customAdjustment():Rectangle { 
   >               /* Your custom adjustment here */ 
   >               [...] 
   >       } 
   >}
   >```

1. Wijs uw implementatie toe aan de `MediaPlayerView` eigenschap.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Voeg uw mening aan het `view` bezit van Media Player toe.

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**Bijvoorbeeld: Schaal de video om de volledige videomening te vullen, zonder aspectverhouding te handhaven:**

```
package com.adobe.mediacore.samples.utils { 
    import com.adobe.mediacore.view.MediaPlayerViewScalePolicy; 
    import flash.geom.Rectangle; 
 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
 
        /** 
        * Default constructor. 
        */ 
        public function CustomScalePolicy() { 
        } 
 
        public function adjust(viewPort:Rectangle, 
                               videoWidth:Number,  
                               videoHeight:Number):Rectangle { 
            return viewPort; 
        } 
    } 
} 
 
var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
view.scalePolicy = new CustomScalePolicy(); 
addChild(view); 
mediaPlayer.view = view;
```

