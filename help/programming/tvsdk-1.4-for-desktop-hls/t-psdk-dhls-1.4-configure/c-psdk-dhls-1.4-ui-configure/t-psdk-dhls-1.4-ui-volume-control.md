---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
seo-description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
seo-title: Volumeregeling opgeven
title: Volumeregeling opgeven
uuid: c51e99b6-efd1-414e-9ef7-77bd53e0d6c0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# Verstrek volumeregeling{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht tot de instantie MediaPlayer een geldige status voor deze opdracht heeft.

   Elke status behalve RELEASED is geldig.
1. Roep de volumesetmethode op de instantie `MediaPlayer` aan om het audiovolume in te stellen.

   ```
   public function set volume(value:Number):void
   ```

   De waarde voor het volume geeft het gevraagde volume weer, uitgedrukt in verhouding tot het maximale volume, waarbij 0 stil is en 1 het maximale volume.

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> Als het opgegeven volume </th> 
      <th colname="col2" class="entry"> Het resulterende volume is </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> Minder dan 0 </td> 
      <td colname="col2"> 0 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Tussen 0 en 1 </td> 
      <td colname="col2"> Het opgegeven volume </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Groter dan 1 </td> 
      <td colname="col2"> De waarde gedeeld door 100 en ingesteld op een van de volgende waarden: 
      <ul id="ul_8C2282F0EDC44A408820F5768709214F"> 
      <li id="li_B00BC6F4812D4000891358F762C8E492">Het resultaat als dit tussen 0 en 1 ligt </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">1 als het resultaat groter is dan 1 </li> 
      </ul> <p>Tip:  Deze logica handelt waarden af die van cliënten worden geleverd die op vroegere versies van worden gebaseerd 
      <span class="codeph">zinnen/primetime-sdk-name</span>, waarbij de volumewaarden varieerden van 0 tot 100. </p> </td> 
   </tr> 
   </tbody> 
   </table>
