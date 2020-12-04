---
description: Deze klassen beschrijven uw mediaspeler en de bijbehorende bronnen.
seo-description: Deze klassen beschrijven uw mediaspeler en de bijbehorende bronnen.
seo-title: Mediaspelers, klassen
title: Mediaspelers, klassen
uuid: 6b59dcff-9722-4a84-9049-f6f10f7b3e82
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# Mediaspelklassen {#media-player-classes}

U kunt de objectief-C API van de Speler Primetime gebruiken om het gedrag van de speler aan te passen.

Deze klassen beschrijven uw mediaspeler en de bijbehorende bronnen.

<table frame="all" colsep="1" rowsep="1" id="table_bm2_wl2_2m"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>Klasse</b> </td> 
   <td colname="2"><b>Beschrijving</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTABRControlParameters.html" format="html" scope="external"> PTABRControlParameters</a></span> </td> 
   <td colname="2">Hiermee worden alle adaptieve parameters voor bitsnelheid ingekapseld. Ondersteunde parameters zijn: 
    <ul id="ul_pnh_hm2_2m"> 
     <li id="li_46572FE1EB514AFF8C9F731E44DAF30B"><span class="codeph"> minBitRate</span> </li> 
     <li id="li_A10C75C9A5234241A5B84A4139F4D143"><span class="codeph"> maxBitRate</span> </li> 
     <li id="li_4E77E367A2E848D2B3E1A9C52209A7B2"><span class="codeph"> initialBitRate</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDefaultMediaPlayerClientFactory.html" format="html" scope="external"> PTDefaultMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> Standaardimplementatie van <span class="codeph"> PTMediaPlayerClientFactory</span> in de TVSDK. Het verstrekt de beschikbare <span class="codeph"> PTOpportunityResolver</span>, <span class="codeph"> PTContentResolver</span>, en <span class="codeph"> PTAdPolicySelector</span> instanties. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html" format="html" scope="external"> PTMediaPlayer</a></span> </td> 
   <td colname="2">Definieert de basiscomponent voor het Primetime Player-framework. <p>Toepassingen maken een instantie van deze klasse om media af te spelen. Deze component verzendt meldingen om de toepassing op elk gewenst moment te laten weten wat de status van de speler is. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTMediaPlayerClientFactory.html" format="html" scope="external"> PTMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> Protocol dat de methoden beschrijft die een aangepaste mediaspeler-clientfabriek moet implementeren om de beschikbare <span class="codeph"> PTOpportunityResolver</span>-, <span class="codeph"> PTContentResolver</span>- en <span class="codeph"> PTAdPolicySelector</span>-instanties te leveren. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerItem.html" format="html" scope="external"> PTMediaPlayerItem</a></span> </td> 
   <td colname="2"> Vertegenwoordigt een specifieke audio-videomedia. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerView.html" format="html" scope="external"> PTMediaPlayerView</a></span> </td> 
   <td colname="2"> Beheert de weergavecomponent van het Primetime Player-framework. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaProfile.html" format="html" scope="external"> PTMediaProfile</a></span> </td> 
   <td colname="2"> Vertegenwoordigt het profiel van één enkele stroom in de variant playlist. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaSelectionOption.html" format="html" scope="external"> PTMediaSelectionOption</a></span> </td> 
   <td colname="2">Vertegenwoordigt een audiovisuele mediabron die geschikt is voor verschillende taalvoorkeuren, toegankelijkheidsvereisten of aangepaste toepassingsconfiguraties. Geldige optietypen: 
    <ul id="ul_p2q_gn2_2m"> 
     <li id="li_46BE5AE49732481FB6D336FFF896E5AD">Ondertitels (<span class="codeph"> PTMediaSelectionOptionTypeSubtitle</span>) </li> 
     <li id="li_6CEADCA12D4A48B7AE4A539985F32119">Alternatieve audio (<span class="codeph"> PTMediaSelectionOptionTypeAudio</span>) </li> 
     <li id="li_248D3D997F8A4B6E9B48869F84060D1F"> <p>Ongedefinieerd (<span class="codeph"> PTMediaSelectionOptionTypeUndefined</span>) </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTOpportunityResolver.html" format="html" scope="external"> </a> </span> PTOportunityResolverclass,  <span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolver.html" format="html" scope="external"> </a> PTOportResolverprotocol</span> </td> 
   <td colname="2"> Klasse die wordt gebruikt voor de verwerking van aanwijzingen in manifest die als plaatsen voor Adobe Primetime en besluitvormingsproces zullen worden gebruikt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolverDelegate.html" format="html" scope="external"> PTOplementityResolverDelegate</a></span> </td> 
   <td colname="2"> Protocol dat de methodes beschrijft die de oplosser van de douanemogelijkheid ( <span class="codeph"> PTOportunityResolver</span>) zou moeten gebruiken om aan de afgevaardigde het statuut van het oplossen van de kans mee te delen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDK.html" format="html" scope="external"> PTSDK</a></span> </td> 
   <td colname="2"> Beschrijft de versie van TVSDK en zijn mogelijkheden. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDKConfig.html" format="html" scope="external"> PTSDKConfig</a></span> </td> 
   <td colname="2"> Hiermee worden algemene instellingen voor TVSDK beschikbaar gemaakt en kan een toepassing zich abonneren op aangepaste HLS-tags. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTTextStyleRule.html" format="html" scope="external"> PTTextStyleRule</a></span> </td> 
   <td colname="2"> Definieert constanten die kenmerksleutels voor tekststijlen vertegenwoordigen die het regelwoordenboek vormen. </td> 
  </tr> 
 </tbody> 
</table>

