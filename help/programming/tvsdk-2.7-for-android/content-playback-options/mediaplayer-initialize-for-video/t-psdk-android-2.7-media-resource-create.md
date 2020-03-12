---
description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
seo-description: De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
seo-title: Een mediabron maken
title: Een mediabron maken
uuid: f34a11a3-dac2-405e-8632-1d9617cc019d
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Een mediabron maken {#create-a-media-resource}

Voor elke nieuwe video-inhoud initialiseert u een MediaResource-instantie met informatie over de video-inhoud en laadt u de mediabron.

De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.

1. Maak een mediabestand `MediaResource` door informatie over de media door te geven aan de `MediaResource` constructor.

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
      <td colname="col2"> Één van de volgende leden van <span class="codeph"> MediaResource.Type </span> enum, die aan het vermelde dossiertype beantwoordt: 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - ISO-indeling voor basismediabestanden (MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - MPEG-DASH media Presentation Description (MPD) </li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> metagegevens </span> </td> 
      <td colname="col2"> Een instantie van de <span class="codeph"> </span> klasse Metagegevens (een woordenboekachtige structuur) die aanvullende informatie kan bevatten over de inhoud die op het punt staat te worden geladen, zoals alternatieve inhoud of inhoud die in de hoofdinhoud moet worden geplaatst. Als u reclame gebruikt, stelt u AuditudeSettings in <span class="codeph"> voordat u deze constructor gebruikt (zie </span> <a keyref="ad-insertion-metadata"></a>). </td> 
      </tr> 
      </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK ondersteunt het afspelen van alleen bepaalde typen inhoud. Als u een ander type inhoud probeert te laden, verzendt TVSDK een foutgebeurtenis.
   >
   >Voor MP4-video-on-demand (VOD)-inhoud biedt TVSDK geen ondersteuning voor truc&#39;s, ABR-streaming (Adaptive bit rate), invoeging, Closed Captions of DRM.

   Met de volgende code wordt een `MediaResource` instantie gemaakt:

   ```java
   // To do: Create metadata here 
   MediaResource res = new MediaResource( 
     "https://www.example.com/video/some-video.m3u8",  
     MediaResource.Type.HLS, 
     metadata); 
   ```

   Na deze stap kunt u op elk gewenst moment `MediaResource` accessors (getters) gebruiken om het type, de URL en de metagegevens van de bron te bekijken.

1. Laad de mediabron met een van de volgende opties:

   * De instantie MediaPlayer.
   * `MediaPlayerItemLoader` Zie Een mediabron [laden met MediaPlayerItemLoader](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md)voor meer informatie.
   >[!IMPORTANT]
   >
   >Laad de mediabron niet op een achtergrondthread. De meeste verrichtingen TVSDK moeten op de belangrijkste draad lopen, en het runnen van hen op een achtergronddraad kan de verrichting veroorzaken om een fout te werpen en weg te gaan.
