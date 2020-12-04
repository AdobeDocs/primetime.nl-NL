---
description: Uw toepassing kan de activiteit in uw speler en de veranderende staat van de speler controleren door naar gebeurtenissen te luisteren die door TVSDK worden verzonden.
seo-description: Uw toepassing kan de activiteit in uw speler en de veranderende staat van de speler controleren door naar gebeurtenissen te luisteren die door TVSDK worden verzonden.
seo-title: Gebeurtenissen van Playback
title: Gebeurtenissen van Playback
uuid: 6d6491d7-cf25-4130-8388-68b8c028bb71
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Afspeelgebeurtenissen {#playback-events}

Uw toepassing kan de activiteit in uw speler en de veranderende staat van de speler controleren door naar gebeurtenissen te luisteren die door TVSDK worden verzonden.

TVSDK verzendt afspeelgebeurtenissen wanneer afspeelbewerkingen van media plaatsvinden, zoals een video die wordt afgespeeld. Registreer listeners bij het `MediaPlayer`-object voor de volgende gebeurtenissen om een melding over alle aan het afspelen gerelateerde gebeurtenissen te ontvangen.

<table frame="all" colsep="1" rowsep="1" id="table_922EEA3DE0BD47BA982E11F890CA0A6B"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Gebeurtenis </th> 
   <th colname="2" class="entry"> Betekenis </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Afspelen</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_SELECTED" format="html" scope="external"> RATE_SELECTED</a> </td> 
   <td colname="2"> De gebruiker of TVSDK heeft een nieuwe afspeelsnelheid geselecteerd, zoals vooruitspoelen, terugspoelen of het afspelen met een normale snelheid hervatten. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_PLAYING" format="html" scope="external"> RATE_PLAYING</a> </td> 
   <td colname="2"> Er wordt een nieuwe afspeelsnelheid weergegeven op het scherm. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> TimeChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html#TIME_CHANGED" format="html" scope="external"> TIME_CHANGED</a> </td> 
   <td colname="2"> De huidige positie van de afspeelkop van het medium is gewijzigd. Wordt periodiek verzonden wanneer de huidige tijd is gewijzigd, elke 250 ms of meer. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Mediaspeler</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerStatus ChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html#STATUS_CHANGED" format="html" scope="external"> STATUS_CHANGED</a> </td> 
   <td colname="2"> De status van de mediaspeler is gewijzigd. Uw toepassing moet fouten in de callback van deze gebeurtenis afhandelen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfileEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> PROFILE_CHANGED</a> </td> 
   <td colname="2">Het huidige profiel van de mediaspeler is gewijzigd. Gebruik de eigenschap <span class="codeph"> ProfileEvent.profile</span> om het nieuwe profiel op te halen dat wordt afgespeeld. Gebruik de eigenschap <span class="codeph"> time</span> om de tijd op te halen waarop deze gebeurtenis plaatsvond. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaplayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">Gebeurtenis MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEM_CREATED</a> </td> 
   <td colname="2">Er is een <span class="codeph"> MediaPlayerItem</span> gemaakt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">Gebeurtenis MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEM_BIJGEWERKT</a> </td> 
   <td colname="2">De mediaspeler heeft de media in de volgende gevallen bijgewerkt: 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">Wanneer manifest verfrist zich voor een levende activa voorkomt. </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">Wanneer een VOD of een actief element ondertiteling heeft gesloten en de activiteit eerst voor een gesloten ondertitelingsspoor wordt ontdekt. </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Bijschriften en audio</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Gebeurtenis MediaPlayerItem.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">Er is een nieuwe Closed Captioning-track gedetecteerd in de mediastream en de verzameling <span class="codeph"> closedCaptionsTracks</span> is bijgewerkt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Manifest en tijdlijn</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">De mediaspeler heeft advertenties toegevoegd of verwijderd en heeft dus een bijgewerkte tijdlijn. <p>Het manifest dat is vernieuwd voor een actief en oude advertentieonderbrekingen zijn verwijderd uit de tijdlijn of er zijn nieuwe advertentiemogelijkheden (actiepunten) ontdekt. De mediaspeler probeert nieuwe advertenties op te lossen en op de tijdlijn te plaatsen. </p> <p> Gebruik deze gebeurtenis om te controleren of de tijdlijn updates bevat (VOD verandert niet tijdens het afspelen). Vervolgens kunt u de tijdlijn ophalen met <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> MediaPlayer.timeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

