---
description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en Browser-TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
seo-description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en Browser-TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
seo-title: banneradvertenties weergeven
title: banneradvertenties weergeven
uuid: aabc126e-b3aa-42dd-ab50-a7db8e324c50
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# banneradvertenties {#display-banner-ads} weergeven

Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en Browser-TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.

Browser TVSDK biedt een lijst met banneradvertenties die zijn gekoppeld aan een lineaire advertentie via de gebeurtenis `AdobePSDK.PSDKEventType.AD_STARTED`.

Manifests kunnen banneradvertenties voor gezellen specificeren door:

* Een HTML-fragment
* De URL van een iFrame-pagina
* De URL van een statische afbeelding of een Adobe Flash-SWF-bestand

Voor elke bijbehorende advertentie geeft Browser TVSDK aan welke typen beschikbaar zijn voor uw toepassing.

Voeg een listener toe voor de gebeurtenis `AdobePSDK.PSDKEventType.AD_STARTED` die het volgende doet:
1. Wist bestaande advertenties in de bannerinstantie.
1. Haalt de lijst met bijbehorende advertenties op van `Ad.getCompanionAssets`.
1. Doorloop de lijst voor bannerinstanties als de lijst met bijbehorende advertenties niet leeg is.

   Elke bannerinstantie (een `AdBannerAsset`) bevat informatie, zoals breedte, hoogte, middeltype (html, iframe, of statisch), en gegevens die worden vereist om de bijbehorende banner te tonen.
1. Als een video zonder bijbehorende advertenties is geboekt, bevat de lijst met bijbehorende elementen geen gegevens voor die video-advertentie.
1. Verzendt de bannergegevens naar een functie op de pagina die de banners op een geschikte locatie weergeeft.

   Dit is gewoonlijk een `div`, en uw functie gebruikt `div ID` om de banner te tonen. Bijvoorbeeld:

   Voeg de gebeurtenislistener toe:

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   De listener-handler implementeren:

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void 
   { 
       // check if there are any companion banner 
       if (event.ad && event.ad.companionAssets  
                    && event.ad.companionAssets.length > 0) { 
            for each (var banner:AdBannerAsset in event.ad.companionAssets) { 
               if (ExternalInterface.available) { 
                   //-- call the java script that will handle the banner display. 
                   ExternalInterface.call('addBanner', banner.resourceType,  
                       banner.width, banner.height, banner.bannerData); 
                } 
            } 
        }  
        //...        
   }
   ```

   Voorbeeld van JavaScript om de weergave af te handelen:

   ```js
   function displayCompanion (resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
       var bannerDiv = document.getElementById('banner' + width + 'x' + height);  
   
       // Assuming that there is an HTML element on the page  
       // with an id of "banner300x250", for example 
       if (bannerDiv !== null) { 
           bannerDiv.innerHTML = data; 
       } 
   }
   ```

