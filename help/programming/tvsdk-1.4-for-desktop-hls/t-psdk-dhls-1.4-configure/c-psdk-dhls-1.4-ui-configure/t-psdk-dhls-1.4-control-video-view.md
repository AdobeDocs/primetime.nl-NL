---
description: U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.
title: De positie en grootte van de videoweergave bepalen
exl-id: 5e7ae557-7f2b-4697-85eb-e72d1f43a7fc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# De positie en grootte van de videoweergave bepalen{#control-the-position-and-size-of-the-video-view}

U kunt de positie en grootte van de videoweergave bepalen met het MediaPlayerView-object.

TVSDK probeert standaard de hoogte-breedteverhouding van de videoweergave te behouden wanneer de grootte of de positie van de video verandert (als gevolg van een wijziging die door de toepassing, een profielschakelaar of een inhoudsschakelaar is aangebracht, enz.).

U kunt het standaardgedrag voor de verhouding overschrijven door een andere waarde op te geven *schaalbeleid*. Geef het schaalbeleid op met de opdracht `MediaPlayerView` object `scalePolicy` eigenschap. De `MediaPlayerView`Het standaardschaalbeleid van de gebruiker wordt ingesteld met een instantie van het `MaintainAspectRatioScalePolicy` klasse. Als u het schaalbeleid opnieuw wilt instellen, vervangt u de standaardinstantie van `MaintainAspectRatioScalePolicy` op `MediaPlayerView.scalePolicy` met uw eigen beleid. (U kunt de `scalePolicy` naar een null-waarde.)

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
   >
   ```
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

1. Uw weergave toevoegen aan de `view` eigenschap.

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
