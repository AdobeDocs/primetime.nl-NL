---
description: De inhoud van een AdAsset beschrijft een bijbehorende banner.
title: Bannergegevens van de onderneming
exl-id: fae96cb8-0092-43ed-a26b-cdaa1389a368
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Bannergegevens van de onderneming {#companion-banner-data}

De inhoud van een AdAsset beschrijft een bijbehorende banner.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

Elk `AdAsset` biedt informatie over de weergave van het element.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>Beschikbare informatie </b></th> 
   <th colname="col2" class="entry"> <b>Beschrijving</b> </th> 
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
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> statische URL </td> 
   <td colname="col2"> <p>Soms heeft de bijbehorende banner ook een <span class="codeph"> staticURL</span> dat een directe URL is naar de afbeelding of naar een <span class="codeph"> .swf</span> (flitsbanner). </p> <p>Als u html of iframe niet wilt gebruiken, kunt u een directe URL naar een afbeelding of SWF gebruiken om de banner in plaats daarvan in het werkgebied van de Flash weer te geven. In dit geval kunt u de opdracht <span class="codeph"> staticURL</span> om de banner weer te geven. </p> <p>Belangrijk: U moet controleren of de statische URL een geldige tekenreeks is, omdat deze eigenschap mogelijk niet altijd beschikbaar is. </p> </td> 
  </tr> 
 </tbody> 
</table>
