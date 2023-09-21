---
description: Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en Browser-TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.
title: banneradvertenties weergeven
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# banneradvertenties weergeven {#display-banner-ads}

Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en Browser-TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.

Browser TVSDK biedt een lijst met banneradvertenties die zijn gekoppeld aan een lineaire advertentie via de `AdobePSDK.PSDKEventType.AD_STARTED` gebeurtenis.

Manifests kunnen banneradvertenties voor gezellen specificeren door:

* Een HTML-fragment
* De URL van een iFrame-pagina
* De URL van een statisch of Adobe Flash-SWF-bestand

Voor elke bijbehorende advertentie geeft Browser TVSDK aan welke typen beschikbaar zijn voor uw toepassing.

Een listener toevoegen voor de gebeurtenis `AdobePSDK.PSDKEventType.AD_STARTED` dat doet het volgende:
1. Wist bestaande advertenties in de bannerinstantie.
1. Hiermee wordt de lijst met bijbehorende advertenties opgehaald van `Ad.getCompanionAssets`.
1. Doorloop de lijst voor bannerinstanties als de lijst met bijbehorende advertenties niet leeg is.

   Elke bannerinstantie (een `AdBannerAsset`) bevat informatie, zoals breedte, hoogte, middeltype (html, iframe, of statisch), en gegevens die wordt vereist om de bijbehorende banner te tonen.
1. Als een video zonder bijbehorende advertenties is geboekt, bevat de lijst met bijbehorende elementen geen gegevens voor die video-advertentie.
1. Verzendt de bannergegevens naar een functie op de pagina die de banners op een geschikte locatie weergeeft.

   Dit is meestal een `div`en uw functie gebruikt de `div ID` de banner weergeven. Bijvoorbeeld:

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
