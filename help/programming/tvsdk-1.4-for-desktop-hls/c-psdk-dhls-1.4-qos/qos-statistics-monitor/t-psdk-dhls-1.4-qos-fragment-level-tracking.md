---
description: U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van de klasse lezen LoadInformation.
seo-description: U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van de klasse lezen LoadInformation.
seo-title: Bijhouden op fragmentniveau met behulp van laadgegevens
title: Bijhouden op fragmentniveau met behulp van laadgegevens
uuid: 41fb2b90-3531-4cc5-bf9b-01ccae04d2fd
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Bijhouden op fragmentniveau met behulp van laadgegevens{#track-at-the-fragment-level-using-load-information}

U kunt de kwaliteit van de dienst (QoS) informatie over gedownloade middelen, zoals fragmenten en sporen, van de klasse lezen LoadInformation.

1. Implementeer de `onLoadInformationAvailable` callback-gebeurtenislistener.

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. Registreer de gebeurtenislistener, die door TVSDK wordt aangeroepen telkens wanneer een fragment is gedownload.

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. Lees de gegevens van belang van de `LoadInformation` die tot callback wordt overgegaan.

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> Eigenschap </th> 
      <th colname="col1" class="entry"> Type </th> 
      <th colname="col2" class="entry"> Beschrijving </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration </span> </td> 
      <td colname="col1"> <p>Getal </p> </td> 
      <td colname="col2"> <p>De duur van de download in milliseconden. </p> <p>TVSDK maakt geen onderscheid tussen de tijd dat de client verbinding heeft gemaakt met de server en de tijd die nodig was om het volledige fragment te downloaden. Bijvoorbeeld, als een 10 MB segment 8 seconden aan download vergt, verstrekt TVSDK die informatie, maar vertelt u niet dat het 4 seconden tot de eerste byte en nog eens 4 seconden kostte om het volledige fragment te downloaden. </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <p>Getal </p> </td> 
      <td colname="col2"> De mediaduur van de gedownloade fragmenten in milliseconden. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> size </span> </td> 
      <td colname="col1"> <p>Getal </p> </td> 
      <td colname="col2"> De grootte van de gedownloade bron in bytes. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> de index van het overeenkomstige spoor, indien bekend; anders, 0. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> de naam van de overeenkomstige spoorbaan, indien bekend; anders, null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> het type van het overeenkomstige spoor, indien bekend; anders, null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> Wat heeft TVSDK gedownload. Een van de volgende opties: 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST - Een afspeellijst/manifest </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT - Een fragment </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK - Een fragment dat is gekoppeld aan een specifieke track </li> 
      </ul> Soms is het mogelijk dat het type van de bron niet kan worden gedetecteerd. Als dit gebeurt, wordt FILE geretourneerd. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <p>String </p> </td> 
      <td colname="col2"> De URL die naar de gedownloade bron wijst. </td> 
   </tr> 
   </tbody> 
   </table>
