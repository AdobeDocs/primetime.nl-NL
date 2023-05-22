---
description: TVSDK ondersteunt het weergeven van lineaire VPAID-advertenties (Video Player-Ad Interface Definition) in een ad-break. VPAID versie 1.0 vereist Flash, terwijl versie 2.0 ook werkt met Browser-TVSDK en JavaScript.
title: Lineaire VPAID-advertenties weergeven in een advertentiescheiding
exl-id: 316a38ac-ec2d-498c-b441-304e2fa75993
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Lineaire VPAID-advertenties weergeven in een advertentiescheiding{#display-linear-vpaid-ads-in-an-ad-break}

TVSDK ondersteunt het weergeven van lineaire VPAID-advertenties (Video Player-Ad Interface Definition) in een ad-break. VPAID versie 1.0 vereist Flash, terwijl versie 2.0 ook werkt met Browser-TVSDK en JavaScript.

U moet een advertentiecontainer opgeven ( `AdContainerView`) binnen de `MediaPlayerContext` -instantie.

Beperkingen voor VPAID-advertenties:

* VPAID-advertenties hebben niet noodzakelijkerwijs een vooraf gedefinieerde duur, aangezien de advertentie interactief kan zijn. Daarom komt de duur van de advertentie (gedefinieerd door de reactie van de advertentieserver) mogelijk niet altijd exact overeen met de werkelijke duur van de advertentie.
* Voor VPAID 1.0-advertenties moet voor TVSDK de Flash-speler 14.0.0.160 of hoger op het apparaat zijn geïnstalleerd. Voor eerdere versies van de Flash-speler is deze functie uitgeschakeld en worden VPAID 1.0-advertenties overgeslagen.

Een advertentiecontainer instellen voor de weergave van VPAID-advertenties (versie 1.0 of 2.0) binnen een advertentiepakket:

1. Gebruik de volgende voorbeeldcode om een advertentiecontainer in te stellen die VPAID-advertenties kan weergeven.

   ```
   var context:MediaPlayerContext =  
     new MediaPlayerContext(_authorizedFeatureHelper.authorizedFeatures); 
   
   adContainer = new AdContainerView(); 
   adContainer.x = adContainer.y = 0; 
   adContainer.setSize(videoContainer.width, videoContainer.height); 
   addChild(adContainer); 
   
   context.adContainer = adContainer; 
   _player = new DefaultMediaPlayer(context);
   ```

1. Wanneer de weergave groter of kleiner wordt, herstelt u de grootte van de advertentiecontainer.

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >Wanneer u een gebeurtenis voor het volledig wijzigen van het scherm krijgt en u de nieuwe grootte instelt op de advertentiecontainer, geeft u de weergavestatus van het werkgebied als volgt door om ervoor te zorgen dat de grootte van de speler op de juiste wijze wordt gewijzigd:
   >
   >
   ```
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```
