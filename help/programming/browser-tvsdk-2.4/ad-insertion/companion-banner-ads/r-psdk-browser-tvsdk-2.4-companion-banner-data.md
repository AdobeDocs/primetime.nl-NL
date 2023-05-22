---
description: De inhoud van een AdBannerAsset beschrijft een bijbehorende banner.
title: Bannergegevens van de onderneming
exl-id: 94954233-4357-43be-a61f-6d8010c930ca
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Bannergegevens van de onderneming{#companion-banner-data}

De inhoud van een AdBannerAsset beschrijft een bijbehorende banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

De `AdobePSDK.PSDKEventType.AD_STARTED` gebeurtenis retourneert een `Ad` instantie die een `companionAssets` eigenschap ( `Array<AdBannerAsset>`).
Elk `AdBannerAsset` biedt informatie over de weergave van het element.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Beschikbare informatie </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Breedte van de bijbehorende banner in pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Hoogte van de bijbehorende banner in pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> brontype </td> 
   <td colname="col2">Het middeltype voor deze metgezelbanner: 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: De gegevens staan in HTML-code. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: De gegevens zijn een iframe-URL (src). </li> 
     <li id="li_48E74AC5F00640EC8A4DE2CB31E106EC">statisch: De gegevens zijn een URL (src) voor statische afbeeldingen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">
    <pre>
      bannergegevens
    </pre> </td> 
   <td colname="col2"> De gegevens van het type dat wordt opgegeven door <span class="codeph"> resourceType</span> voor deze gezelschapsbanner. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Soms heeft de bijbehorende banner ook een staticURL die een directe URL naar de afbeelding is. </p> <p>Als u geen html of iframe wilt gebruiken, kunt u een directe URL aan een afbeelding gebruiken. In dit geval kunt u de staticURL gebruiken om de banner weer te geven. </p> <p>Belangrijk: U moet controleren of de statische URL een geldige tekenreeks is, omdat deze eigenschap mogelijk niet altijd beschikbaar is. </p> </td> 
  </tr> 
 </tbody> 
</table>
