---
description: TVSDK verzendt afspeelgebeurtenissen wanneer afspeelbewerkingen van media plaatsvinden, zoals een video die wordt afgespeeld.
title: Gebeurtenissen van Playback
exl-id: 675dd444-d58c-4316-9d62-b64e6433b650
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Gebeurtenissen van Playback{#playback-events}

TVSDK verzendt afspeelgebeurtenissen wanneer afspeelbewerkingen van media plaatsvinden, zoals een video die wordt afgespeeld.

Registreer een implementatie van `MediaPlayer.PlaybackEventListener`, inclusief de volgende callbacks van gebeurtenissen.

<table frame="all" colsep="1" rowsep="1"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Gebeurtenis </th> 
   <th colname="2" class="entry"> Betekenis </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Afspelen</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayComplete%28%29" format="html" scope="external"> onPlayComplete</a> </td> 
   <td colname="2"> Het einde van een mediabron is bereikt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayStart%28%29" format="html" scope="external"> onPlayStart</a> </td> 
   <td colname="2"> Het afspelen van een mediabron is gestart. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRateSelected%28float%29" format="html" scope="external"> onRateSelected</a> (variabele rente) </td> 
   <td colname="2"> De gebruiker of TVSDK heeft een nieuwe afspeelsnelheid geselecteerd, zoals vooruitspoelen, terugspoelen of het afspelen met een normale snelheid hervatten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRatePlaying%28float%29" format="html" scope="external"> onRatePlay</a> (variabele rente) </td> 
   <td colname="2"> Er wordt een nieuwe afspeelsnelheid weergegeven op het scherm. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Media</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPrepared%28%29" format="html" scope="external"> onPrepared</a> </td> 
   <td colname="2"> De mediaspeler heeft de media met succes voorbereid. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onSizeAvailable%28long,%20long%29" format="html" scope="external"> onSizeAvailable</a> (lange hoogte, lange breedte) </td> 
   <td colname="2"> De grootte van de media is beschikbaar. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Mediaspeler</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onStateChanged%28com.adobe.mediacore.MediaPlayer.PlayerState,com.adobe.mediacore.MediaPlayerNotification%29" format="html" scope="external"> onStateChanged</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlayerState.html" format="html" scope="external"> MediaPlayer.PlayerState</a> staat, <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html" format="html" scope="external"> MediaPlayerNotification</a> kennisgeving) </td> 
   <td colname="2"> De status van de mediaspeler is gewijzigd. De toepassing moet fouten in deze callback afhandelen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onProfileChanged%28long,%20long%29" format="html" scope="external"> onProfileChanged</a> (lang profiel, lange tijd) </td> 
   <td colname="2"> Het huidige profiel van de mediaspeler is gewijzigd. Gebruik de <span class="codeph"> Profiel</span> om het nieuwe profiel op te halen dat wordt afgespeeld. Gebruik de <span class="codeph"> tijd</span> eigenschap om de tijd op te halen waarop deze gebeurtenis heeft plaatsgevonden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>MediaplayerItem</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onUpdated%28%29" format="html" scope="external"> onUpdated</a> </td> 
   <td colname="2">De mediaspeler heeft de media in de volgende gevallen bijgewerkt: 
    <ul> 
     <li>Wanneer manifest verfrist zich voor een levende activa voorkomt.</li> 
     <li>Wanneer een VOD of een actief element ondertiteling heeft gesloten en de activiteit eerst voor een gesloten ondertitelingsspoor wordt ontdekt. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Manifest en tijdlijn</b></td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimedMetadata%28com.adobe.mediacore.metadata.TimedMetadata%29" format="html" scope="external"> onTimedMetadata</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html" format="html" scope="external"> TimedMetadata</a> timeMetadata) </td> 
   <td colname="2"> Er worden nieuwe metagegevens met tijdinstelling in het manifest gedetecteerd. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated%28%29" format="html" scope="external"> onTimelineUpdated</a> </td> 
   <td colname="2">De mediaspeler heeft advertenties toegevoegd of verwijderd en heeft dus een bijgewerkte tijdlijn. <p>Het manifest dat is vernieuwd voor een actief en oude advertentieonderbrekingen zijn verwijderd uit de tijdlijn of er zijn nieuwe advertentiemogelijkheden (actiepunten) ontdekt. De mediaspeler probeert nieuwe advertenties op te lossen en op de tijdlijn te plaatsen. </p><p> Gebruik deze gebeurtenis om te controleren of de tijdlijn updates bevat (VOD verandert niet tijdens het afspelen). U kunt de tijdlijn vervolgens ophalen met <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html#getTimeline%28%29" format="html" scope="external"> MediaPlayer.getTimeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
