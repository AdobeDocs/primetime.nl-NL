---
description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
title: De positie en grootte van de videoweergave bepalen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# De positie en grootte van de videoweergave bepalen{#control-the-position-and-size-of-the-video-view}

U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.

TVSDK probeert standaard de hoogte-breedteverhouding van de videoweergave te behouden wanneer de grootte of de positie van de video verandert (als gevolg van een wijziging die door de toepassing, een profielschakelaar of een inhoudsschakelaar is aangebracht, enz.).

U kunt het standaardgedrag voor de verhouding overschrijven door een andere waarde op te geven *schaalbeleid*. Geef het schaalbeleid op met de opdracht `MediaPlayerView` object `scalePolicy` eigenschap. De `MediaPlayerView`Het standaardschaalbeleid van de gebruiker wordt ingesteld met een instantie van het `MaintainAspectRatioScalePolicy` klasse. Vervang de standaardinstantie van `MaintainAspectRatioScalePolicy` op `MediaPlayerView.scalePolicy` met uw eigen beleid. (U kunt de instelling `scalePolicy` naar een null-waarde.)

1. Implementeer de `MediaPlayerViewScalePolicy` om uw eigen schaalbeleid te maken.

   De `MediaPlayerViewScalePolicy` heeft één methode:

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK gebruikt een `StageVideo` -object voor het weergeven van de video en omdat `StageVideo` de objecten staan niet in het weergaveoverzicht, `viewPort` parameter bevat de absolute coördinaten van de video.
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
   >

1. Uw implementatie toewijzen aan de `MediaPlayerView` eigenschap.

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Uw weergave toevoegen aan de mediaspeler `view` eigenschap.

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**Bijvoorbeeld: schaal de video om de volledige videoweergave te vullen, zonder de hoogte-breedteverhouding te behouden:**

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
