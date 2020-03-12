---
description: TVSDK biedt ondersteuning voor banneradvertenties die bij een lineaire advertentie horen en die vaak op de pagina blijven staan nadat de lineaire advertentie is beëindigd. Uw toepassing is verantwoordelijk voor het weergeven van de bijbehorende banners die een lineaire advertentie hebben.
seo-description: TVSDK biedt ondersteuning voor banneradvertenties die bij een lineaire advertentie horen en die vaak na afloop van de lineaire advertentie op de pagina blijven staan. Uw toepassing is verantwoordelijk voor het weergeven van de bijbehorende banners die een lineaire advertentie hebben.
seo-title: Companion banneradvertenties
title: Companion banneradvertenties
uuid: 388a1683-342c-4f3b-97c8-cfcb6c5cfee1
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Companion banneradvertenties {#companion-banner-ads}

TVSDK biedt ondersteuning voor banneradvertenties die bij een lineaire advertentie horen en die vaak na afloop van de lineaire advertentie op de pagina blijven staan. Uw toepassing is verantwoordelijk voor het weergeven van de bijbehorende banners die een lineaire advertentie hebben.

Volg deze aanbevelingen bij het weergeven van bijhorende advertenties:

* Poging om zoveel van de banneradvertenties van een video-advertentie weer te geven als in de lay-out van de speler passen.
* Een bijbehorende banner alleen presenteren als u een locatie hebt die exact overeenkomt met de opgegeven hoogte en breedte.

   >[!TIP]
   >
   >Wijzig de grootte van de banner niet.

* Plaats de bijbehorende banner(s) zo snel mogelijk nadat de advertentie is gestart.
* Bedek de hoofd-advertentie-/videoclip niet met bijbehorende banners.
* Ga door met het weergeven van bijbehorende banners nadat de advertentie is beëindigd.

   Standaard wordt elke bijbehorende banner weergegeven totdat u een nieuwe banner voor deze banner hebt.

## Bannergegevens van de onderneming {#companion-banner-data}

De inhoud van een AdBannerAsset beschrijft een bijbehorende banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

De `AdPlaybackEvent.AD_STARTED` gebeurtenis retourneert een `Ad` instantie die een `companionAssets` eigenschap ( `Vector.<AdAsset>`) bevat.
Elk element `AdAsset` biedt informatie over de weergave van het element.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Beschikbare informatie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Breedte van de bijbehorende banner in pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Hoogte van de bijbehorende banner in pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> brontype </td> 
   <td colname="col2">Het middeltype voor deze metgezelbanner: 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: De gegevens zijn in HTML-code. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: De gegevens zijn een iframe-URL (src). </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> bannergegevens </td> 
   <td colname="col2"> De gegevens van het type dat door <span class="codeph"> resourceType</span> voor deze metgezelbanner wordt gespecificeerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Soms heeft de bijbehorende banner ook een staticURL die een directe URL naar de afbeelding of naar een <span class="filepath"> .swf</span> (flash banner) is. </p> <p>Als u html of iframe niet wilt gebruiken, kunt u een directe URL naar een afbeelding of SWF gebruiken om de banner in het Flash-werkgebied weer te geven. In dit geval kunt u de staticURL gebruiken om de banner weer te geven. </p> <p>Belangrijk:  U moet controleren of de statische URL een geldige tekenreeks is, omdat deze eigenschap mogelijk niet altijd beschikbaar is. </p> </td> 
  </tr> 
 </tbody> 
</table>

## banneradvertenties weergeven {#display-banner-ads}

Als u banneradvertenties wilt weergeven, moet u bannerinstanties maken en TVSDK toestaan te luisteren naar gebeurtenissen met betrekking tot advertenties.

TVSDK biedt een lijst met banneradvertenties die zijn gekoppeld aan een lineaire advertentie via de `AdPlaybackEvent.AD_STARTED` gebeurtenisgebeurtenis.

Manifests kunnen banneradvertenties voor gezellen specificeren door:

* Een HTML-fragment
* De URL van een iFrame-pagina
* De URL van een statische afbeelding of een Adobe Flash SWF-bestand

Voor elke bijbehorende advertentie geeft TVSDK aan welke typen beschikbaar zijn voor uw toepassing.

Voeg een listener toe voor de `AdPlaybackEvent.AD_STARTED` gebeurtenis die het volgende doet:

1. Wist bestaande advertenties in de bannerinstantie.

1. Haalt de lijst met bijbehorende advertenties op van `Ad.companionAssets`.

1. Doorloop de lijst voor bannerinstanties als de lijst met bijbehorende advertenties niet leeg is.

   Elke bannerinstantie ( `AdBannerAsset`) bevat informatie, zoals breedte, hoogte, middeltype (html, iframe of statisch), en gegevens die worden vereist om de bijbehorende banner weer te geven.

1. Als een video zonder bijbehorende advertenties is geboekt, bevat de lijst met bijbehorende elementen geen gegevens voor die video-advertentie.

   Als u een standalone weergaveadvertentie wilt weergeven, voegt u de logica toe aan uw script om een normale DFP-advertentie (DoubleClick voor Publishers) in de juiste bannerinstantie uit te voeren.

1. Verzendt de bannergegevens naar een functie op uw pagina, meestal JavaScript, door te gebruiken `ExternalInterface`, die de banners op een geschikte locatie weergeeft.

   Dit is meestal een `div`bewerking en uw functie gebruikt deze `div ID` om de banner weer te geven. Bijvoorbeeld:

   Voeg de gebeurtenislistener toe:

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   De listener-handler implementeren:

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void { 
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
   function addBanner(resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
   
   //Assume an html element on the page with id like 'banner300x250' 
       var bannerDiv = document.getElementById('banner' + width +  
           'x' + height);  
       if (bannerDiv != null) { 
           if (resourceType == "html") { // for html resource 
               bannerDiv.innerHTML = data; 
           } 
           else if (resourceType == "iframe") { // for iframe resource 
               bannerDiv.innerHTML = "<iframe src='" + data +  
                   "' width='100%' height='100%'></iframe>"; 
           } 
       } 
   }
   ```
