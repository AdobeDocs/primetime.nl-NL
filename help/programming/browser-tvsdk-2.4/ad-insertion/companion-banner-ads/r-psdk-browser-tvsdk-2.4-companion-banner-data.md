---
description: De inhoud van een AdBannerAsset beschrijft een bijbehorende banner.
seo-description: De inhoud van een AdBannerAsset beschrijft een bijbehorende banner.
seo-title: Bannergegevens van de onderneming
title: Bannergegevens van de onderneming
uuid: b2c709da-9d19-49d1-8116-9c947371b77c
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Companion banner data{#companion-banner-data}

De inhoud van een AdBannerAsset beschrijft een bijbehorende banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

De gebeurtenis `AdobePSDK.PSDKEventType.AD_STARTED` retourneert een `Ad`-instantie die een `companionAssets`-eigenschap ( `Array<AdBannerAsset>`) bevat.
Elke `AdBannerAsset` biedt informatie over de weergave van het element.

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
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html: De gegevens zijn in HTML-code. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe: De gegevens zijn een iframe-URL (src). </li> 
     <li id="li_48E74AC5F00640EC8A4DE2CB31E106EC">statisch: De gegevens zijn een URL (src) voor statische afbeeldingen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">
    <pre>
      bannergegevens
    </pre> </td> 
   <td colname="col2"> De gegevens van het type dat door <span class="codeph"> resourceType</span> voor deze metgezelbanner wordt gespecificeerd. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Soms heeft de bijbehorende banner ook een staticURL die een directe URL naar de afbeelding is. </p> <p>Als u geen html of iframe wilt gebruiken, kunt u een directe URL aan een afbeelding gebruiken. In dit geval kunt u de staticURL gebruiken om de banner weer te geven. </p> <p>Belangrijk:  U moet controleren of de statische URL een geldige tekenreeks is, omdat deze eigenschap mogelijk niet altijd beschikbaar is. </p> </td> 
  </tr> 
 </tbody> 
</table>

