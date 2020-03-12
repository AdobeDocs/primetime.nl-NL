---
description: Wanneer de media speler zijn huidige profiel aan een nieuw profiel overschakelt, kunt u informatie over de schakelaar terugwinnen, met inbegrip van wanneer het geschakeld, breedte en hoogteinformatie, of waarom een verschillende beetjetarief werd gebruikt.
seo-description: Wanneer de media speler zijn huidige profiel aan een nieuw profiel overschakelt, kunt u informatie over de schakelaar terugwinnen, met inbegrip van wanneer het geschakeld, breedte en hoogteinformatie, of waarom een verschillende beetjetarief werd gebruikt.
seo-title: Informatie ophalen over profielschakelaar
title: Informatie ophalen over profielschakelaar
uuid: 0ff1aeac-882a-4209-b19f-1aa3141404d9
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Informatie ophalen over profielschakelaar{#get-information-about-profile-switch}

Wanneer de media speler zijn huidige profiel aan een nieuw profiel overschakelt, kunt u informatie over de schakelaar terugwinnen, met inbegrip van wanneer het geschakeld, breedte en hoogteinformatie, of waarom een verschillende beetjetarief werd gebruikt.

1. Luister naar de `AdobePSDK.PSDKEventType.PROFILE_CHANGED` gebeurtenis.

   De Browser TVSDK-mediaspeler verzendt deze gebeurtenis wanneer het adaptieve algoritme voor het wisselen van bitsnelheid overschakelt naar een ander profiel vanwege netwerk- of computeromstandigheden. (Wanneer de bitsnelheid of de punt verandert.)
1. Wanneer de gebeurtenis voorkomt, controleer de volgende eigenschappen voor informatie over de schakelaar:

   * `profile`: Id voor het nieuwe profiel dat wordt gebruikt.
   * `time`: De stroomtijd waarbij de schakelaar voorkwam.
   * `description`: Een tekstbeschrijving van de reden voor een wijziging van de bitsnelheid, als een tekenreeks met door puntkomma&#39;s gescheiden sleutel/waardeparen. Bevat maximaal één `Reason` en één `Bitrate`. Als de informatie niet beschikbaar is of de bitsnelheid niet is gewijzigd, is deze tekenreeks leeg.
   <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Sleutelnaam </th> 
      <th colname="col2" class="entry"> Mogelijke waarden </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Reden </span> </td> 
      <td colname="col2"> 
        <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
        <li id="li_E374B029E1AF40689D70A9D30E057C5B">Netwerkaanpassing </li> 
        <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">Seek </li> 
        <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">Profiel wordt niet ondersteund </li> 
        <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">Failover </li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Bitsnelheid </span> </td> 
      <td colname="col2"> 
        <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
        <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> omhoog </span>: De bitsnelheid is verhoogd </li> 
        <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> omlaag </span>: De bitsnelheid is verlaagd </li> 
        </ul> </td> 
      </tr> 
    </tbody> 
    </table>

   Hier volgen enkele voorbeelden van geretourneerde `description` tekenreeksen:

   ```
   "Bitrate::=up;Reason::=Network Adaptation;" 
   
   "Bitrate::=down;Reason::=Failover;"
   ```

   * `width`: Geheel getal dat de breedte in pixels aangeeft.
   * `height`: Geheel getal dat de hoogte in pixels aangeeft.
   >[!NOTE]
   >
   >Breedte- en hoogtegegevens zijn alleen beschikbaar als ze zijn opgenomen in het `RESOLUTION` label in het M3U8-manifest. Als de informatie niet in de M3U8 is opgenomen, worden de eigenschappen width en height ingesteld op 0, aangezien deze geen deel uitmaken van de profielinformatie.
