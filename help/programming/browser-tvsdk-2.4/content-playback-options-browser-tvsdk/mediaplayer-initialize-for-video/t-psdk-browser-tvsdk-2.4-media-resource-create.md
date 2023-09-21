---
description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
title: Een mediabron maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Een mediabron maken {#create-a-media-resource}

De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.

1. Een `MediaResource` door informatie over de media aan de `MediaResource` constructor.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
    <tr> 
    <th colname="col1" class="entry"> Constructorparameter </th> 
    <th colname="col2" class="entry"> Beschrijving </th> 
    </tr> 
    </thead>
    <tbody> 
    <tr> 
    <td colname="col1"> <p>url </p> </td> 
    <td colname="col2"> <p>Een tekenreeks die de URL van het manifest of de afspeellijst van het medium vertegenwoordigt. </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>Een van de volgende leden van de <span class="codeph"> MediaResource.Type </span> opsomming die overeenkomt met het opgegeven bestandstype: </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - ISO-indeling voor basismediabestanden (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metagegevens </p> </td> 
    <td colname="col2"> <p>Een instantie van de <span class="codeph"> Metagegevens </span> klasse, die aangepaste informatie over de te laden inhoud kan bevatten. Voorbeelden van inhoud zijn alternatieve inhoud of voegt inhoud toe die in de hoofdinhoud wordt geplaatst. Als u reclame gebruikt, instellen <span class="codeph"> AuditudeSettings </span> voordat u deze constructor gebruikt. Zie voor meer informatie <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Advertentie-toevoeging-meta-gegevens</a>. </p> <p>Tip: U kunt de Flash indien nodig terugdraaien met de <span class="codeph"> forceFlash </span> parameter wanneer het creëren van een media middel. Dit kan handig zijn omdat momenteel niet alle functies (zoals Live Adflows) worden ondersteund in TVSDK van de browser. Flash fallback wordt gebruikt om video-inhoud af te spelen. </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >Browser-TVSDK ondersteunt het afspelen van alleen bepaalde typen inhoud. Als u probeert een ander type inhoud te laden, verzendt Browser TVSDK een foutgebeurtenis.

   De volgende code maakt een `MediaResource` -instantie:

   ```js
   //create a MediaResource instance pointing to some HLS content 
   Metadata metadata = //TODO: create metadata here 
   mediaResource = new AdobePSDK.MediaResource ( 
         "https://www.example.com/video/some-video.m3u8", 
         AdobePSDK.MediaResourceType.HLS,  
         metadata);
   ```

   >[!TIP]
   >
   >U kunt op elk gewenst moment daarna `MediaResource` accessors (getters) om het type, de URL en de metagegevens van de bron te bekijken.

1. Laad de instantie MediaPlayer. Zie voor meer informatie [Een mediabron laden in de MediaPlayer](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md).
