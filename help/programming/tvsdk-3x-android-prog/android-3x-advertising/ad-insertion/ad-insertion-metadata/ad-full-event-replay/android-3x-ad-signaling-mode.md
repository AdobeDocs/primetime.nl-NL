---
description: De ad-signaliseringsmodus bepaalt waar de videostream advertentie-informatie moet ophalen.
seo-description: De ad-signaliseringsmodus bepaalt waar de videostream advertentie-informatie moet ophalen.
seo-title: Toevoegingsmodus
title: Toevoegingsmodus
uuid: 947544f9-667e-4d81-af83-155f0db7788e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Toevoegingsmodus {#ad-signaling-mode}

De ad-signaliseringsmodus bepaalt waar de videostream advertentie-informatie moet ophalen.

De geldige waarden zijn `DEFAULT`, `SERVER_MAP`en `MANIFEST_CUES`.

In de volgende tabel wordt het effect beschreven van `AdSignalingMode` waarden voor de verschillende typen HLS-streams:

<table frame="all" colsep="1" rowsep="1" id="table_AdSignalingMode"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> </th> 
   <th colname="2" class="entry"> <b>Standaard </b></th> 
   <th colname="3" class="entry"><b> Manifest cues</b> </th> 
   <th colname="4" class="entry"> <b>Toegevoegde serverkaart </b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Video op aanvraag (VOD) </td> 
   <td colname="2"> 
    <ul id="ul_E79DA79107364D0D8B46A1859CA75B5C"> 
     <li id="li_B259ED87743F463095071F58DC840E39"> Gebruikt serverkaart voor plaatsingsopsporing </li> 
     <li id="li_8957E4151466467BA6C954E5010E34EA"> Advertenties worden ingevoegd </li> 
    </ul> </td> 
   <td colname="3"> 
    <ul id="ul_D462C76717D94DE09915BDF6E9B3FB68"> 
     <li id="li_FB46108F4AD9457D99D2618ABEF7DBD1"> Gebruikt in-stream cues voor plaatsingsdetectie </li> 
     <li id="li_C3F7FBB98F524CEF97D17318C292E9EA"> Pre-roll advertenties worden opgenomen in de hoofdstroom </li> 
     <li id="li_A56E1545F84840DFA6D065DA60E98C31"> De hoofdstroom wordt vervangen door middelste rollen </li> 
    </ul> </td> 
   <td colname="4"> 
    <ul id="ul_F10192B1B6F745CBB0D4C1A6D52A57B4"> 
     <li id="li_2ADACF71FA5F4A08A00A3399F5593420"> Gebruikt serverkaart voor plaatsingsopsporing </li> 
     <li id="li_1201085B9C554A4BBD471E7EB2E363AC"> Advertenties worden ingevoegd </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> Live/lineair </td> 
   <td colname="2"> 
    <ul id="ul_82AAC9EE056F49E999F809536A96C2F8"> 
     <li id="li_73BAD2BAA95F4592808B77F8DA436237"> Gebruikt duidelijke aanwijzingen voor plaatsingsdetectie </li> 
     <li id="li_A97B6F61078D4149A984B2412021E103"> Extra vervangen hoofdstroom </li> 
    </ul> </td> 
   <td colname="3"> 
    <ul id="ul_CAED2D4F46334D76AE025482881BF843"> 
     <li id="li_A8023845A037482DBFDEF7EF247FECFD"> Gebruikt in-stream cues voor plaatsingsdetectie </li> 
     <li id="li_62A3CDAD249344EB89043B2AE0F4D7FF"> Extra vervangen hoofdstroom </li> 
    </ul> </td> 
   <td colname="4"> Niet ondersteund </td> 
  </tr> 
 </tbody> 
</table>