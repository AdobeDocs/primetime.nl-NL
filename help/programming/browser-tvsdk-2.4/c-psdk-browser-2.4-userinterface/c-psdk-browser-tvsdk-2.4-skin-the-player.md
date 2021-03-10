---
description: U kunt de volgende informatie gebruiken om u te helpen een skin aan uw speler toewijzen. Voor elke visuele constructie, wordt het overeenkomstige gedrag vermeld in standaardgedrag.
title: De speler Skins toewijzen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---


# De speler {#skinning-the-player} vegen

U kunt de volgende informatie gebruiken om u te helpen een skin aan uw speler toewijzen. Voor elke visuele constructie, wordt het overeenkomstige gedrag vermeld in standaardgedrag.

>[!IMPORTANT]
>
>De skindetails in dit document zijn voor de standaardelementen UI die door het kader UI worden gecreeerd. Als de speler deze elementen heeft gewijzigd, moeten ook de skinelementen worden gewijzigd.

## Containerdiv {#section_99B0D598219D4150B57E97D5381B118F}

Hier volgen de stijlen voor de containerdiv-elementen:

>[!TIP]
>
>Deze div-elementen worden vermeld in het `common-styles.css`-bestand.

Hier volgen de stijlen voor de hoofddiv:

<table id="table_AC5745DF725543ADBBCD68BA6130DF12"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Main Div</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-main-video-div-stijl</span> </td> 
   <td colname="col2"> <p>De stijl van het belangrijkste div waarin de video speelt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .pip-modus-actief</span> </td> 
   <td colname="col2"> <p>Wordt gebruikt wanneer de PIP-modus actief is. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Het standaardgedrag is <span class="codeph"> videoBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Beeld-in-beeld (PIP)</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-pip-video-div</span> </td> 
   <td colname="col2"> <p>De stijl van het div-element waarin PIP-video wordt afgespeeld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .view-as-main-video</span> </td> 
   <td colname="col2"> <p>Wordt toegepast op het eerste PIP wanneer het is omgewisseld en wordt weergegeven als de hoofdvideo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Weergave van meerdere video's</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-view-container</span> </td> 
   <td colname="col2"> <p>Wordt gebruikt in de weergave met meerdere video's. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multiview-weergave</span> </td> 
   <td colname="col2"> <p>Een algemene CSS-stijl die op elke video in de multiview wordt geplaatst. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multiview</span> </td> 
   <td colname="col2"> <p>Wanneer de container waarin alle video's zijn opgeslagen in meerdere weergaven, in meerdere weergaven wordt weergegeven. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Verschillende besturingselementen {#section_E9E4A8E3AEBF4BDC89840B84B3B0E737}

Hier volgen de stijlen voor algemene besturingselementen voor spelers:

>[!TIP]
>
>Deze stijlen worden vermeld in het `default-controls.css` dossier.

<table id="table_0ACB6BAB5DAD42DBBD18CA7C0385A261"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-controle</span> </td> 
   <td colname="col2"> <p>Van toepassing op alle besturingselementen op de bedieningsbalk, met uitzondering van scrubber en spatie </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-input-slider</span> </td> 
   <td colname="col2"> <p>Invoerschuifregelaars </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-header</span> </td> 
   <td colname="col2"> <p>Koptekst van de deelvensters </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-vertical-list-menu-item</span> </td> 
   <td colname="col2"> <p>Menulijst in verticale stijl </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-fill-spacer</span> </td> 
   <td colname="col2"> <p>Ruimte op besturingsbalk </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-hr-separator</span> </td> 
   <td colname="col2"> <p>Scheidingsteken voor horizontale lijnen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-title</span> </td> 
   <td colname="col2"> <p>Titel van de deelvensters </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-close-btn</span> </td> 
   <td colname="col2"> <p>Knop voor het sluiten van het deelvenster </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-button-background</span> </td> 
   <td colname="col2"> <p>Achtergrond van alle knoppen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-txt-control</span> </td> 
   <td colname="col2"> <p>Standaardstijlen voor tekstbesturingselementen. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Regelbalk {#section_B683B51EC746484B9AA90CB481D637BD}

Hier volgen de stijlen voor de besturingsbalk:

<table id="table_681E13F264674F849FAA2523EB65F094"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control-bar</span>  (standaardgedrag)</td>
   <td colname="col2"> <p>Van toepassing op de bedieningsbalk </p> </td> 
  </tr> 
 </tbody> 
</table>

## Functieknoppen {#section_57FFD242FF674EA2867BCF6CA7F6B855}

>[!NOTE]
>
>De letters in de volgende tabellen komen overeen met de letters in deze afbeelding.

Hier volgen de stijlen voor de scrubbalk:

<table id="table_2207AD72E72A47FFA03AC748F06A54FD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl (A) </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar</span> </td> 
   <td colname="col2"> <p>Werkbalk op besturingsbalk </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-buffer-progress-bar</span> </td> 
   <td colname="col2"> <p>De voortgangsbalk van de buffer op de scrubbalk </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-seek-to-bar</span> </td> 
   <td colname="col2"> <p>Status van de scrubbalk wanneer de gebruiker erop zoekt </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-playback-progress-bar</span> </td> 
   <td colname="col2"> <p>Status van de scrubbalk tijdens normaal afspelen </p> </td> 
  </tr>
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-progress-bar-play-head</span> </td>
   <td colname="col2"> <p>Kop afspelen op scrubbalk tijdens afspelen </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-ad-marker-bar</span> </td>
   <td colname="col2"> <p>Advertentiemarkering </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-scrub-bar.ptp-ad-marker</span> </td>
   <td colname="col2"> <p>Advertentiemarkering </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is:

* `scrubBarBehavior`
* `bufferProgressBarBehavior`
* `playHeadBehavior`
* `playProgressBarBehavior`
* `seekToBarBehavior`

## Knop Afspelen/Pauzeren {#section_F1F40A948D0049C5A4D8EA5F2A475CAA}

Hier volgen de stijlen voor de knop Afspelen/Pauzeren:

<table id="table_975C2293222A4782A8C75A6149C1AD27">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (B) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause</span> </td>
   <td colname="col2"> <p>De knop Pauze afspelen op de besturingsbalk. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-btn-</span> playpausin de pauzestatus </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td> 
   <td colname="col2"> <p><span class="codeph"> ptp-btn-</span> playpausin de afspeelstatus </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `playPauseButtonBehavior`.

## Volume {#section_23E17BD2343948F8A2CEE1C8BEE2F874}

Hier zijn de stijlen om de volumeknoop te vormen:

<table id="table_8F9831F36A4D427CA31C9FFA4173170D">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (C) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><span class="codeph"> .ptp-volumeregeling</span>
     <ul id="ul_B12ADDFB83EA40FD8B4E92AF418AA4B4">
      <li id="li_7DA8143A69ED4E7D8A560B9FF75D6BA7"><span class="codeph"> .extended</span> </li>
      <li id="li_D8CCAD45D81C4850B6903FE261833AE6"><span class="codeph"> .vertical</span> </li>
     </ul> </p> </td>
   <td colname="col2"> <p>Volumeregeling op besturingsbalk
     <ul id="ul_2C60F018FDCB458885738AC378C02F61">
      <li id="li_6B19572B504A4BBF9C97DC29C0E92A1D">Als het besturingselement zich in de uitgevouwen vorm bevindt </li>
      <li id="li_6489E422E1944D5194CBDFC8383D2F30">Wanneer het besturingselement in verticale vorm is </li>
     </ul> </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume</span> </td>
   <td colname="col2"> <p>Knop Volume op besturingsbalk </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.min-volume-state</span> </td>
   <td colname="col2"> <p>Wanneer volume in minimumtoestand is </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.mute-state</span> </td>
   <td colname="col2"> <p>Wanneer volume in stilte staat </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `volumeBehavior` en `muteButtonBehavior`.

Hier volgen de stijlen voor de volumeschuifregelaar:

<table id="table_E3DC93F8FC614C30AADAE259D18F10EF">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (D) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-schuifregelaar</span> </td>
   <td colname="col2"> <p>De volumeschuifregelaar. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-hidden</span> </td>
   <td colname="col2"> <p>De volumeschuifregelaar in een verborgen status. </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `volumeSliderBehavior`.

## {#section_06EE608FC54A4CF5B5DF9DC743CFC740} terugspoelen

Hier is de stijl voor de knop Terugspoelen:

<table id="table_0ACB116582D54B188E9F5B5C03D3A615">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (E) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>De knop Terugspoelen op de besturingsbalk. </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `rewindButtonBehavior`.

## Tijd {#section_0E6549B3DF6D4C10947D445A5F8EEA7F}

Hier is de stijl om de resterende tijd op de besturingsbalk weer te geven:

<table id="table_CEE62BFF5FB04FDCBBE1331E0D727EBA">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (F) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-txt-display-time</span> </td>
   <td colname="col2"> <p>Geeft de resterende tijd op de besturingsbalk weer </p> </td>
  </tr>
</tbody>
</table>

Het standaardgedrag is `timeRemainingBehavior`.

## Snel terugspoelen {#section_F6E6C65BD3BD493A89915DF9B92933BA}

Hier is de stijl voor de knop Snel terugspoelen:

<table id="table_25BB4966B709402383AB6A6822FC1999">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (G) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>De knop Snel terugspoelen op de besturingsbalk. </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `fastRewindButtonBehavior`.

## Langzaam terugspoelen {#section_38A22BB8681B430F8C6808C3BD21FB4E}

Hier is de stijl voor de knop Langzaam terugspoelen:

<table id="table_E623C374622A497C91E22333D77AF8F6">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (H) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowrewind</span> </td>
   <td colname="col2"> <p>De knop Langzaam terugspoelen op de besturingsbalk. </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `slowRewindButtonBehavior`.

## Volgende langzaam {#section_92ACF092EECC4A5EAF6AA090C05E552E}

Hier is de stijl voor de langzame voorwaartse knoop:

<table id="table_88C1CF5DB2D84EDBA01AC62B70509B08">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (I) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowaakse</span> </td>
   <td colname="col2"> <p>De langzame voorwaartse knoop op de controlebar. </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `slowForwardButtonBehavior`.

## Snel vooruitspoelen {#section_F90ED8B3739B49ACAB1F12DF18F0E4D6}

Hier is de stijl voor de knop Snel vooruit:

<table id="table_F166BD1E8B934B34AF3690BBBAD894B7">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl (J) </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastforward</span> </td>
   <td colname="col2"> <p>De snelle voorwaartse knoop op de controlebar. </p> </td>
  </tr>
 </tbody>
</table>

Het standaardgedrag is `fastForwardButtonBehavior`.

## Audiotrack {#section_1CDF4FA5A1C14DB6B9C96579FFA1057C}

Hier zijn de stijlen om het audiospoor te vormen:

<table id="table_22FC521D786B45EB84F230894FFECE79">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Knop Audiotrack (K)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-audio-track</span> </td>
   <td colname="col2"> <p>De knop voor de audiotrack op de besturingsbalk. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Het standaardgedrag is <span class="codeph"> audioTrackButtonBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Deelvenster Selectie audiotrack (L)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-panel</span> </td> 
   <td colname="col2"> <p>Het deelvenster voor het selecteren van de audiotrack. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Het standaardgedrag is <span class="codeph"> audioTrackSelectionPanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Selectiekop audiotrack (M)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>De header voor de <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Selectiemenu audiotrack (N)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-menu</span> </td>
   <td colname="col2"> <p>De menu-items in <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
 </tbody>
</table>

## {#section_B2ADC76E76304A68AD648A00A12B676E} delen

Hier zijn de stijlen om het delen te vormen:

<table id="table_3264C472809D462B8FC16680B96B1AC9">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Knop voor delen van sociale media (O)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video</span> </td> 
   <td colname="col2"> <p>De knop Delen via sociale media op de besturingsbalk waarmee <span class="codeph"> ptp-share-video-panel</span> wordt geopend. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Het standaardgedrag is <span class="codeph"> shareVideoButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Deelvenster Video delen (P)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel</span> </td>
   <td colname="col2"> <p>Het deelvenster waarin de opties voor sociaal delen worden weergegeven. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Het standaardgedrag is <span class="codeph"> shareVideoPanelBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Menu Video delen (Q)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>De header voor de <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .share-video-panel-menu</span> </td>
   <td colname="col2"> <p>Het menu in <span class="codeph"> ptp-share-video-panel</span> dat alle opties toont om inhoud op sociale media te delen. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel-menu-item</span> </td>
   <td colname="col2"> <p>Het menu-item in het <span class="codeph"> share-video-panel-menu</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-facebook</span> </td>
   <td colname="col2"> <p>Het menu-item waarmee u inhoud kunt delen op Facebook. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-twitter</span> </td>
   <td colname="col2"> <p>Het menu-item waarmee u inhoud kunt delen op Twitter. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-google-plus</span> </td>
   <td colname="col2"> <p>Het menu-item waarmee u inhoud kunt delen op Google Plus. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-linkedin</span> </td>
   <td colname="col2"> <p>Het menu-item waarmee u inhoud kunt delen op LinkedIn. </p> </td>
  </tr>
 </tbody>
</table>

## Ondertiteling {#section_A01BA68218564DA0B7D6BF51F045D7AB}

Hier zijn de stijlen om gesloten titels te vormen:

<table id="table_777C7034C9424F8C841DABD480FFAC47">
 <thead>
  <tr>
   <th colname="col1" class="entry"> Stijl </th>
   <th colname="col2" class="entry"> Beschrijving </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>Knop Ondertiteling (R)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-closed-caption</span> </td>
   <td colname="col2"> <p>De <span class="uicontrol"> Gesloten Captions</span> knoop op de controlebar. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Het standaardgedrag is <span class="codeph"> closedCaptionButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .on-state</span> </td>
   <td colname="col2"> <p>De bijschriften zijn ingeschakeld voor een video. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Deelvenster Ondertiteling (S)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-panel</span> </td>
   <td colname="col2"> <p>Het deelvenster voor gesloten bijschriften. </p> </td>
  </tr>
  <tr>
   <td colname="col1">Het standaardgedrag is <span class="codeph"> closedCaptionLanguagePanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>Talen met gesloten bijschriften (T)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-panel:</span> </td>
   <td colname="col2"> <p>De header voor de <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-menu:  </span> </td>
   <td colname="col2"> <p>Het menu in het venster met gesloten bijschriften. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>Opties voor Closed Captions (U)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-btn</span> </td>
   <td colname="col2"> <p>De <span class="uicontrol"> knoop van Opties</span> in het gesloten paneel van de opties van titels. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-panel</span> </td>
   <td colname="col2"> <p>Het deelvenster Opties van het deelvenster met gesloten bijschriften. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-menu-item</span> </td>
   <td colname="col2"> <p>Het menu-item in het deelvenster met gesloten bijschriften. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .selected</span> </td>
   <td colname="col2"> <p>In het geselecteerde frame. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-done-btn</span> </td> 
   <td colname="col2"> <p>De <span class="uicontrol"> Gereed</span> knoop in de kopbal van het gesloten paneel van de opties van titels. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-menu</span> </td> 
   <td colname="col2"> <p>Het menu Opties in gesloten bijschriften. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-main-menu</span> </td> 
   <td colname="col2"> <p>Het hoofdmenu voor de opties voor gesloten bijschriften. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-sub-menu</span> </td> 
   <td colname="col2"> <p>Het submenu voor de opties voor gesloten bijschriften. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-opacity-slider</span> </td> 
   <td colname="col2"> <p>De schuifregelaar Dekking voor opties voor gesloten bijschriften. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-menu-separator</span> </td> 
   <td colname="col2"> <p>Het scheidingsteken voor Closed Caption-opties. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-menu-item</span> </td> 
   <td colname="col2"> <p>Het gesloten bijschrift <span class="uicontrol"> Opties</span> menupunt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-preview-panel</span> </td> 
   <td colname="col2"> <p>Het voorvertoningsvenster voor gesloten bijschriften. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-footer</span> </td> 
   <td colname="col2"> <p>De voettekst van de opties voor gesloten bijschrift. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-reset-button</span> </td> 
   <td colname="col2"> <p>De <span class="uicontrol"> knoop van het Terugstellen</span> in footer van het gesloten paneel van de opties van de titel. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-apply-button</span> </td> 
   <td colname="col2"> <p>Met de knop <span class="uicontrol"> Toepassen</span> in de voettekst van het venster met opties voor een gesloten bijschrift. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Het standaardgedrag is <span class="codeph"> closedCaptionOptionsPanelBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Meer opties (V) {#section_18E25CF8A8964FFD9026A8A833089CE3}

Hier zijn de stijlen om extra opties te vormen:
<table id="table_EC6EF88E2EDE4B8EBB1C14F87A6161FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options</span> </td> 
   <td colname="col2"> <p>De <span class="uicontrol"> Meer Opties</span> knoop. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options.ptp-control-bar-btn</span> </td> 
   <td colname="col2"> <p>De <span class="codeph"> ptp-btn-more-options</span> die in controlebar worden gebruikt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel</span> </td> 
   <td colname="col2"> <p>Het regelpaneel Meer opties. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu</span> </td> 
   <td colname="col2"> <p>Het menu van het regelpaneel Meer opties. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu-item</span> </td> 
   <td colname="col2"> <p>Het menu-item van het deelvenster Meer opties. </p> </td> 
  </tr> 
 </tbody> 
</table>

Het standaardgedrag is `moreOptionsButtonBehavior`.

## PIP-knop (W) {#section_1EE039DEA99541D391B30BD1DF72A83E}

Hier is de stijl voor de [!UICONTROL PIP<] knoop:

<table id="table_EE2E882C87E24D39B8D5347686F29E55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-pip</span> </td> 
   <td colname="col2"> <p>De knoop van het PIP op de controlebar. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Het standaardgedrag is <span class="codeph"> pipButtonBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## Volledig scherm (X) {#section_158A19DFB30E4432A67E4A74A7CBA563}

Hier is de stijl om het volledige scherm te vormen:

<table id="table_5941835F31AC4E9CBA9702AB8D813B8F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-fullscreen</span> </td> 
   <td colname="col2"> <p>De <span class="uicontrol"> Volledige Scherm</span> knoop op controlebar. </p> </td> 
  </tr> 
 </tbody> 
</table>

Het standaardgedrag is `fullScreenButtonBehavior`.

## Steen afspelen (Y) {#section_AE6F83BB7EE2497FB13CD94A8316192D}

Hier is de stijl om trukspel te vormen:

<table id="table_F1ADAC0A4B4E48669828690BDEB4BC09"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-control-bar-truc-play-rate</span> </td> 
   <td colname="col2"> <p>De component van de de tariefvertoning van de truc in de controlebar. </p> </td> 
  </tr> 
 </tbody> 
</table>

Het standaardgedrag is `trickPlayRateDisplayBehavior`.

## Multiview (Z) {#section_58EFAE7263BA45D3A4E2AB7309A9CAA7}

Hier is de stijl om multiview te vormen:

<table id="table_84B37D7410EE40DFA7A8BB8431C6DCF0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-multiview</span> </td> 
   <td colname="col2"> <p>De <span class="uicontrol"> MultiView</span> knoop op controlebar, en de aanvankelijke staat van <span class="uicontrol"> Multiview</span> knoop. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Het standaardgedrag is <span class="codeph"> multiViewButtonBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
 </tbody> 
</table>

## Miniatuur {#section_0AFD932975634BB08387EEE7D3BFC438}

Hier is de stijl voor het configureren van miniaturen:

<table id="table_968136A8BBA042A7A8E79739B8F92F55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-progress-bar-thumb-nail</span> </td> 
   <td colname="col2"> <p>De voortgangsbalk van de miniaturen. </p> </td> 
  </tr> 
 </tbody> 
</table>

Het standaardgedrag is `thumbnailPreviewBehavior`.

## Foutberichten {#section_AC9858EE1B5A4FF4947E383C663B6AB5}

Hier is de stijl om foutberichten te configureren:

<table id="table_7F4C156170DB4AFFA7DEE06F00449506"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel</span> </td> 
   <td colname="col2"> <p>Het deelvenster waarin de foutberichten van de speler worden weergegeven. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-icon</span> </td> 
   <td colname="col2"> <p>Het pictogram dat in het deelvenster wordt weergegeven wanneer er een foutbericht verschijnt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-message</span> </td> 
   <td colname="col2"> <p>Het foutbericht dat wordt weergegeven. </p> </td> 
  </tr> 
 </tbody> 
</table>

Het standaardgedrag is `errorMessagePanelBehavior`.

## Bedekking bufferen {#section_2FE8FDE2599E42BAA7411D0D38FA0A88}

Hier is de stijl voor het configureren van miniaturen:

<table id="table_1FECE1DC29B8434B886751A29455F004"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-buffering-overlay</span> </td> 
   <td colname="col2"> <p>Het besturingselement voor bufferbedekking. </p> </td> 
  </tr> 
 </tbody> 
</table>

De standaardbedekking is `bufferingOverlayBehavior`.

## Specifieke kiezers {#section_51F735AEF82E41E890FF59E031A0DB89}

Hier is de stijl voor de knop Snel vooruit:

<table id="table_E77EDC7D227348E79C7E73FB5D46F992"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Stijl </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ad-break</span> </td> 
   <td colname="col2"> <p>De status van het bedieningspaneel tijdens het afspelen van de advertentie. </p> <p>Is van toepassing op het volgende: 
     <ul id="ul_D5076303DCD94D968682289823D1A9F2"> 
      <li id="li_4290C4B2D48546E3AD023BED6CAAE395"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_72A3D3E916E44A55BA170407EAB0527D"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_A0BAEBB0E01B402EB83E3CE9B92B15CC"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_FDF2CEDB0A854098907FF9CBCF1A61C1"><span class="codeph"> .ptp-btn-slowaakse</span> </li> 
      <li id="li_CD2E14DB3DD64C10A253DA23FBE04A04"><span class="codeph"> .ptp-btn-slowaakse</span> </li> 
      <li id="li_A230359E8F7F4571A9EBFF0E4C2462D7"><span class="codeph"> .ptp-btn-slowrewind</span> </li> 
      <li id="li_5711A315872F4FA59FDDF0EF0AFD03C6"><span class="codeph"> .ptp-btn-more-options  </span> </li> 
      <li id="li_71C8E76077A84ED590160AB5ABFCC0D7"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_4A3113C0360F4F708AAA96AB316FA057"><span class="codeph"> .ptp-btn-closed-caption  </span> </li> 
      <li id="li_901A0186D65A48A1B774DC555CEC5367"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
      <li id="li_2331583C01C2482B8EE72979FBF111DB"><span class="codeph"> .ptp-btn-pip  </span> </li> 
      <li id="li_7BB39BDF5E294AEB8FA3DCD9F9A29468"><span class="codeph"> .ptp-btn-rewind</span> </li> 
      <li id="li_E4FEF5A7486A40F6A5FE1119BD63AFEF"><span class="codeph"> .ptp-scrub-bar</span> </li> 
      <li id="li_12153547558A4871842EE0416BCCA8B2"><span class="codeph"> .ptp-seek-to-bar</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multi-view</span> </td> 
   <td colname="col2"> <p>De staat van de controle terwijl in multiview. </p> <p>Is van toepassing op het volgende: 
     <ul id="ul_A8AC653C30814AC49041F3B58A2106F4"> 
      <li id="li_0407167DA21647A8A6960DFE55A33F42"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_EA71CAF41CDC41DE859A85CE482BE97C"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_F3A998C51A034C22A914EAEFF19FFEA7"><span class="codeph"> .ptp-btn-closed-caption</span> </li> 
      <li id="li_022F871ABC894C9BA879B3AF3D341202"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .fullscreen-status</span> </td> 
   <td colname="col2"> <p>De speler is in de modus Volledig scherm. </p> <p>Is van toepassing op het volgende: 
     <ul id="ul_B235C1D339F64B2FAC6BC72F03807616"> 
      <li id="li_6E050EE74C604FDAB4C9C0447F547A9D"><span class="codeph"> .ptp-control-bar  </span> </li> 
      <li id="li_67D54B1A41764B2DA544479CDA1C901C"><span class="codeph"> .ptp-btn-fullscreen</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>