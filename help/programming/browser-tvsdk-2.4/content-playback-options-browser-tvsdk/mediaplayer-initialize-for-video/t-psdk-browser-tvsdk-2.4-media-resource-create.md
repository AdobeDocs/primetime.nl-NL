---
description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
seo-description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
seo-title: Een mediabron maken
title: Een mediabron maken
uuid: c25c037e-e9a0-430c-a150-b75a9ac051b1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Een mediabron maken {#create-a-media-resource}

De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.

1. Maak een `MediaResource` door informatie over de media door te geven aan de constructor `MediaResource`.

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
    <td colname="col2"> <p>Een van de volgende leden van de opsomming <span class="codeph"> MediaResource.Type </span> die overeenkomt met het aangegeven bestandstype: </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4  </span> - ISO-indeling voor basismediabestanden (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS  </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH  </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metagegevens </p> </td> 
    <td colname="col2"> <p>Een instantie van de klasse <span class="codeph"> Metadata </span>, die aangepaste informatie kan bevatten over de inhoud die moet worden geladen. Voorbeelden van inhoud zijn alternatieve inhoud of voegt inhoud toe die in de hoofdinhoud wordt geplaatst. Als u reclame gebruikt, stelt u <span class="codeph"> AuditudeSettings </span> in voordat u deze constructor gebruikt. Voor meer informatie, zie <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Advertentie-toevoeging-meta-gegevens</a>. </p> <p>Tip:  U kunt Flash-fallback indien nodig forceren door de parameter <span class="codeph"> forceFlash </span> te gebruiken wanneer u een mediabron maakt. Dit kan handig zijn omdat momenteel niet alle functies (zoals Live Adflows) worden ondersteund in TVSDK van de browser. Flash fallback wordt gebruikt om video-inhoud af te spelen. </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >Browser-TVSDK ondersteunt het afspelen van alleen bepaalde typen inhoud. Als u probeert een ander type inhoud te laden, verzendt Browser TVSDK een foutgebeurtenis.

   De volgende code maakt een `MediaResource`-instantie:

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
   >Op elk ogenblik na dit, kunt u `MediaResource` accessors (getters) gebruiken om het type van middel, URL, en meta-gegevens te onderzoeken.

1. Laad de instantie MediaPlayer. Voor meer informatie, zie [Laad een media middel in MediaPlayer](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md).
