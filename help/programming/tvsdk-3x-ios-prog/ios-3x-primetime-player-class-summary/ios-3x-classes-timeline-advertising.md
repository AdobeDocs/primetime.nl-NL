---
description: Deze klassen bieden informatie over advertenties die binnen een tijdlijn voorkomen.
seo-description: Deze klassen bieden informatie over advertenties die binnen een tijdlijn voorkomen.
seo-title: Tijdlijnadvertentieklassen
title: Tijdlijnadvertentieklassen
uuid: df970e8f-4bf8-4367-9d70-42ebcb11c025
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---


# Tijdlijnadvertentieklassen {#timeline-advertising-classes}

Deze klassen bieden informatie over advertenties die binnen een tijdlijn voorkomen.

<table frame="all" colsep="1" rowsep="1" id="table_1A59E777BA99466793D586286F19E933"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Naam</b></th> 
   <th colname="2" class="entry"><b>Beschrijving</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAd.html" format="html" scope="external"> PTAd</a> </td> 
   <td colname="2">Klasse die de abstractie van de Advertentie bepaalt en alle advertentiemateriaal houdt. Deze wordt gedefinieerd door een unieke id, een duur en een MediaResource. MediaResource bevat URL waar de daadwerkelijke advertentie inhoud verblijft. 
    <pre>
      Vertegenwoordigt een primair lineair element dat in de inhoud wordt gespliceerd. Het kan eventueel een serie van metgezelactiva bevatten die samen met het lineaire element moeten worden getoond.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdAsset.html" format="html" scope="external"> PTAdAsset</a> </td> 
   <td colname="2">Klasse die een element vertegenwoordigt dat moet worden weergegeven. 
    <pre>
      Vertegenwoordigt een element dat moet worden weergegeven.
    </pre> 
    <pre>
      Klasse die een advertentie-element vertegenwoordigt.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBannerView.html" format="html" scope="external"> PTAdBannerView</a> </td> 
   <td colname="2">
    <pre>
      Hiermee geeft u een bannerelement weer. Uw toepassing moet een nieuwe instantie van deze hulpprogrammaklasse maken, het bannerelement instellen en aan een weergave toevoegen. De indruk en klik het volgen voor de banner wordt intern beheerd door deze klasse.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBreak.html" format="html" scope="external"> PTAdBreak</a> </td> 
   <td colname="2">Klasse die een verenigde weergave biedt op meerdere advertenties die op een bepaald punt tijdens het afspelen worden afgespeeld. 
    <pre>
      Vertegenwoordigt een ononderbroken opeenvolging van advertenties die in de inhoud worden gespliceerd.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdClick.html" format="html" scope="external"> PTAdClick</a> </td> 
   <td colname="2">Klasse die een klikinstantie vertegenwoordigt die aan activa wordt geassocieerd. Deze instantie bevat informatie over de doorklikken-URL en de titel die kunnen worden gebruikt om extra informatie aan de gebruiker te verstrekken. 
    <pre>
      Vertegenwoordigt een klikinstantie verbonden aan een middel. Deze instantie bevat informatie over de doorklikken-URL en de titel die kunnen worden gebruikt om extra informatie aan de gebruiker te verstrekken.
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdPolicyInfo.html" format="html" scope="external"> PTAdPolicyInfo</a> </td> 
   <td colname="2"> Protocol dat eigenschappen voor API-aanroepen van AdPolicySelector definieert. Deze eigenschappen bieden de context voor het afdwingen van elk advertentiegedrag. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTAdPolicySelector.html" format="html" scope="external">PTAdPolicySelector</a></td> 
   <td colname="2"> An ad policy selector protocol for enforcing and behavior. De toepassingen kunnen met dit protocol in overeenstemming zijn door alle vereiste methodes uit te voeren of door de bestaande standaard beleidsselecteurscategorie uit te breiden om specifiek gedrag aan te passen. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdTimeline.html" format="html" scope="external">PTAdTimeline</a></td> 
   <td colname="2"> Klasse die de tijdlijn van einden binnen de inhoud vertegenwoordigt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 
    <pre>
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTContentResolver.html" format="html" scope="external"> </a> PTContentResolverclass,  
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolver.html" format="html" scope="external"> </a> PTContentResolverprotocol
    </pre> </td> 
   <td colname="2"> Klasse die het ad-resolving deel in het Adobe Primetime en besluitvormingsproces behandelt. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolverDelegate.html" format="html" scope="external"> PTContentResolverDelegate</a> </td> 
   <td colname="2"> Protocol dat de methodes beschrijft die de oplosser van de douaneinhoud ( <span class="codeph"> PTContentResolver</span>) zou moeten gebruiken om aan de afgevaardigde het statuut van het oplossen van inhoud mee te delen. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Constants/PTPlacementType.html" format="html" scope="external"> PTPlacementType</a> </td> 
   <td colname="2">Klasse die een verzoek om plaatsingsinformatie onttrekt. Aan elke opgeloste advertentie moet één plaatsingsinformatie zijn gekoppeld. De plaatsingsinformatie beschrijft waar de advertentie op de tijdlijn moet worden geplaatst. Het bevat informatie zoals: 
    <ul id="ul_A9105A78F0C24488BCD5E3F2EE62A3EE"> 
     <li id="li_01E968A4330D4B40BA1EB6F4A6000FFD">Plaatsing (in ms) </li> 
     <li id="li_A3DC9498BEE14FBA9E7A5D26874F3984">Type plaatsing (vóór, halverwege of na de rollover) </li> 
     <li id="li_4B9094DD318B4792854A377CC6064232">Duur van het hoofdinhoudsegment dat op het punt staat te worden vervangen </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>