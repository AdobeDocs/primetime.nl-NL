---
description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
title: Een mediabron maken
exl-id: 754515e9-567d-4f9f-911d-e9dad22f71a1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Een mediabron maken {#create-a-media-resource}

Voor elke nieuwe video-inhoud initialiseert u een MediaResource-instantie met informatie over de video-inhoud en laadt u de mediabron.

De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.

1. Een `MediaResource` door informatie over de media aan de `MediaResource` constructor.

   De `MediaResource` constructor vereist de volgende parameters:

   <table id="table_22886D6770FB45E99D35D0B90E6CC302">
      <thead>
      <tr>
      <th colname="col1" class="entry"> Constructorparameter </th>
      <th colname="col2" class="entry"> Beschrijving </th>
      </tr>
      </thead>
      <tbody>
      <tr>
      <td colname="col1"> <span class="codeph"> url </span> </td>
      <td colname="col2"> Een tekenreeks die de URL van het manifest/de afspeellijst van het medium vertegenwoordigt. </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> type </span> </td>
      <td colname="col2"> Een van de volgende leden van de <span class="codeph"> MediaResource.Type </span> Enum, overeenkomend met het opgegeven bestandstype:
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282">
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li>
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - ISO-indeling voor basismediabestanden (MP4) </li>
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - MPEG-DASH Media Presentation Description (MPD) </li>
      </ul> </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> metagegevens </span> </td>
      <td colname="col2"> Een instantie van de <span class="codeph"> Metagegevens </span> klasse (een op een woordenboek lijkende structuur) die aanvullende informatie kan bevatten over de inhoud die wordt geladen, zoals alternatieve inhoud of inhoud die in de hoofdinhoud wordt geplaatst. Als u reclame gebruikt, instellen <span class="codeph"> AuditudeSettings </span> voordat u deze constructor gebruikt. </td>
      </tr>
      </tbody>
   </table>

   >[!IMPORTANT]
   >
   >TVSDK ondersteunt het afspelen van alleen bepaalde typen inhoud. Als u een ander type inhoud probeert te laden, verzendt TVSDK een foutgebeurtenis.
   >
   >Voor MP4-video-on-demand (VOD)-inhoud biedt TVSDK geen ondersteuning voor truc&#39;s, ABR-streaming (Adaptive bit rate), invoeging, Closed Captions of DRM.

   De volgende code maakt een `MediaResource` instantie:

   ```java
   // To do: Create metadata here
   MediaResource res = new MediaResource(
     "https://www.example.com/video/some-video.m3u8",
     MediaResource.Type.HLS,
     metadata);
   ```

   Op elk gewenst moment na deze stap kunt u `MediaResource` accessors (getters) om het type, de URL en de metagegevens van de bron te bekijken.

1. Laad de mediabron met een van de volgende opties:

   * De instantie MediaPlayer.
   * `MediaPlayerItemLoader` Zie voor meer informatie [Een mediabron laden met MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >Laad de mediabron niet op een achtergrondthread. De meeste verrichtingen TVSDK moeten op de belangrijkste draad lopen, en het runnen van hen op een achtergronddraad kan de verrichting veroorzaken om een fout te werpen en weg te gaan.
