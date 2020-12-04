---
description: De MediaPlayer biedt een notifyClick()-functie die aan advertenties gerelateerde gebeurtenissen verzendt wanneer een aanklikbare advertentie wordt afgespeeld. Deze gebeurtenissen bieden informatie over advertenties en afbrekingen die uw app kan gebruiken om doorklikfuncties te bieden.
seo-description: De MediaPlayer biedt een notifyClick()-functie die aan advertenties gerelateerde gebeurtenissen verzendt wanneer een aanklikbare advertentie wordt afgespeeld. Deze gebeurtenissen bieden informatie over advertenties en afbrekingen die uw app kan gebruiken om doorklikfuncties te bieden.
seo-title: Aanklikbare advertenties verwerken
title: Aanklikbare advertenties verwerken
uuid: 5d3c9d36-60d7-4272-a523-7d1fe0e1615f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Klikbare advertenties {#handle-clickable-ads} verwerken

De MediaPlayer biedt een notifyClick()-functie die aan advertenties gerelateerde gebeurtenissen verzendt wanneer een aanklikbare advertentie wordt afgespeeld. Deze gebeurtenissen bieden informatie over advertenties en afbrekingen die uw app kan gebruiken om doorklikfuncties te bieden.

De MediaPlayer voert de volgende gebeurtenissen uit wanneer een klikbare advertentie wordt afgespeeld:

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

`AdClickedEvent` bevat de informatie noodzakelijk om de klikthrough functie te verwerken.

1. Geef gebruikers een besturingselement in de speler op om op klikbare advertenties te klikken.

   Dit kan een knop of een ander element zijn om de klik van de gebruiker vast te leggen.
1. Voeg een gebeurtenislistener toe voor de gebeurtenis ad click van de gebruiker.

   Bijvoorbeeld:

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. Voeg een manager voor de klikgebeurtenis van de gebruiker toe.

   Deze manager moet MediaPlayer ertoe aanzetten om de `AdClicked` gebeurtenis in brand te steken.

   ```
   onAdClick = function (event) { 
       // Get a reference to your player 
       var player = getPlayer(); 
       if (player) { 
           // Call the MediaPlayer's notifyClick function 
           // which gets MediaPlayer to fire AdClicked 
           player.notifyClick(); 
       } 
   } 
   ```

1. Voeg gebeurtenislisteners voor de MediaPlayer toe en begin-, klik- en toevoegde berichten.

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. Voeg gebeurtenishandlers toe.
a. Handel de gebeurtenis voor het starten van de advertentie af.
Dit kan alles doen, zoals het instellen van de gebruikersinterface voor de gebruiker.

   ```
   onAdStarted = function (event) { 
       if (clickAddButton && event && event.ad) { 
           var adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           if (adClick && adClick.isValid) { 
               // Do some initial processing  
               // when the ad starts, prior 
               // to the user's click. 
           } 
       } 
   }
   ```

   b. Handel de gebeurtenis waarop u klikt af.
In dit voorbeeld verkrijgen we advertentiegegevens van de gebeurtenis en openen we een nieuw browservenster met behulp van die informatie:

   ```
   onAdClickedEvent = function (event) { 
       if (event && event.ad) { 
           var adClick = event.adClick; 
           if (!(adClick && adClick.isValid)) { 
               adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           } 
           if (adClick && adClick.isValid) 
           { 
               // Do something with the currently playing ad 
               window.open(adClick.url); 
           } 
       } 
   }
   ```

   c. Handel de gebeurtenis advertentie af.

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
