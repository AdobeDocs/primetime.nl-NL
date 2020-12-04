---
description: Voor elke nieuwe video-inhoud initialiseert u een MediaResource-instantie met informatie over de video-inhoud en laadt u de mediabron. De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
seo-description: Voor elke nieuwe video-inhoud initialiseert u een MediaResource-instantie met informatie over de video-inhoud en laadt u de mediabron. De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.
seo-title: Een mediabron maken
title: Een mediabron maken
uuid: d9fe982a-bedf-445c-b5be-f7918693782a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Een mediabron maken {#create-a-media-resource}

Voor elke nieuwe video-inhoud initialiseert u een MediaResource-instantie met informatie over de video-inhoud en laadt u de mediabron. De MediaResource-klasse vertegenwoordigt de inhoud die door de MediaPlayer-instantie moet worden geladen.

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
    <td colname="col2"> <p>Een van de volgende leden van de opsomming <span class="codeph"> MediaResource.Type </span> die overeenkomt met het aangegeven bestandstype: 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS  </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metagegevens </p> </td> 
    <td colname="col2"> <p>Een instantie van de klasse <span class="codeph"> Metadata </span>, die aangepaste informatie kan bevatten over de inhoud die moet worden geladen. </p> <p>Voorbeelden van inhoud zijn alternatieve inhoud of voegt inhoud toe die in de hoofdinhoud wordt geplaatst. Als u reclame gebruikt, stelt u <span class="codeph"> AuditudeSettings </span> in. Zie <a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local"> Metagegevens Ad Insertion </a> voor meer informatie. </p> </td> 
    </tr> 
    </tbody> 
    </table>

   >[!IMPORTANT]
   >
   >TVSDK ondersteunt het afspelen van alleen bepaalde typen inhoud. Als u een ander type inhoud probeert te laden, verzendt TVSDK een foutgebeurtenis.
   >
   >Voor MP4-video-on-demand (VOD)-inhoud biedt TVSDK geen ondersteuning voor truc&#39;s, ABR-streaming (Adaptive bit rate), invoeging, Closed Captions of DRM.

   De volgende code maakt een `MediaResource`-instantie:

   ```java
   try { 
       // create a MediaResource instance pointing to some HLS content 
       Metadata metadata = //TODO: create metadata  
       MediaResource mediaResource = MediaResource.createFromUrl( 
         "https://www.example.com/video/some-video.m3u8",  
         MediaResource.Type.HLS,  
         metadata); 
   } catch(IllegalArgumentException ex) { 
       // this exception is thrown if the URL does not point  
       // to a valid url. 
   } 
   ```

   >[!TIP]
   >
   >Op dit punt, kunt u `MediaResource` accessors (getters) gebruiken om het type van middel, URL, en meta-gegevens te onderzoeken.

1. Laad de mediabron met behulp van het volgende:

   * Uw MediaPlayer-instantie.

      Voor meer informatie, zie [Laad een media middel in MediaPlayer](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` Voor meer informatie, zie [Laad een media middel gebruikend MediaPlayerItemLoader](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).
   >[!IMPORTANT]
   >
   >Laad de mediabron niet op een achtergrondthread. De meeste verrichtingen TVSDK moeten op de belangrijkste draad worden in werking gesteld, en het runnen van hen op een achtergronddraad kan de verrichting veroorzaken om een fout te werpen en weg te gaan.
