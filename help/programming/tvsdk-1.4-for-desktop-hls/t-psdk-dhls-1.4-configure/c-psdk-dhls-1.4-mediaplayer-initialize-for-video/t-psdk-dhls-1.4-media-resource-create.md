---
description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
title: Een mediabron maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Een mediabron maken {#create-a-media-resource}

Voor elke nieuwe video-inhoud initialiseert u een MediaResource-instantie met informatie over de video-inhoud en laadt u de mediabron.

De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.

1. Een `MediaResource` door informatie over de media aan de `MediaResource` constructor.

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Constructorparameter </th> 
      <th colname="col2" class="entry"> Beschrijving </th> 
      </tr>
    </thead>
    =<tbody> 
      <tr> 
      <td colname="col1"><span class="codeph"> url</span> </td> 
      <td colname="col2"> <p>Een tekenreeks die de URL van het manifest of de afspeellijst van het medium vertegenwoordigt. </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> type</span> </td> 
      <td colname="col2"> <p>Een van de volgende tekenreekswaarden die overeenkomt met het opgegeven bestandstype: 
        <ul id="ul_7512E90B7B294EF9BFBA2D68DE678CBB"> 
        <li id="li_AA84434E84184A3D909552794B425ABD"><span class="codeph"> MP4</span> - ISO-indeling voor basismediabestanden (MP4) </li> 
        <li id="li_8A2F3752569344B59EE30303A8393488"><span class="codeph"> HLS</span> - M3U8 </li> 
        </ul> </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> metagegevens</span> </td> 
      <td colname="col2"> <p>Een instantie van de <span class="codeph"> Metagegevens</span> klasse, die aangepaste informatie over de te laden inhoud kan bevatten. </p> <p>Voorbeelden van inhoud zijn alternatieve inhoud of voegt inhoud toe die in de hoofdinhoud wordt geplaatst. Als u reclame gebruikt, instellen <span class="codeph"> AuditudeSettings</span> voordat u deze constructor gebruikt. Zie voor meer informatie <a href="../../../tvsdk-1.4-for-desktop-hls/ad-insertion/ad-insertion-metadata/c-psdk-dhls-1.4-ad-insertion-metadata.md" format="dita" scope="local"> Ad Insertion-metagegevens</a>. </p> </td> 
      </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK ondersteunt het afspelen van alleen bepaalde typen inhoud. Als u een ander type inhoud probeert te laden, verzendt TVSDK een foutgebeurtenis.
   >
   >Voor MP4-video-on-demand (VOD)-inhoud biedt TVSDK geen ondersteuning voor truc&#39;s, ABR-streaming (Adaptive bit rate), invoeging, Closed Captions of DRM.

   De volgende code maakt een `MediaResource` -instantie:

   ```
   // To do: Create metadata here
   MyResource = new MediaResource(
            "https://www.example.com/video/some-video.m3u8", 
            "HLS",
            MyMetadata)
   ```

   >[!TIP]
   >
   >U kunt nu `MediaResource` accessors (getters) om het type, de URL en de metagegevens van de bron te bekijken.

1. Laad de mediabron met een van de volgende opties:

   * Uw MediaPlayer-instantie.

     Zie voor meer informatie [Laad een media middel in Mediaplayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` Zie voor meer informatie [Laad een media middel in Mediaplayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
