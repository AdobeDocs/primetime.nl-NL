---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumecontrole bieden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Volumecontrole bieden{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht tot de instantie MediaPlayer een geldige status voor deze opdracht heeft.

   Elke status behalve RELEASED is geldig.
1. Roep de methode van de volumeset op `MediaPlayer` -instantie om het audiovolume in te stellen.

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
      </ul> <p>Tip: deze logica handelt waarden af die worden geleverd door clients die zijn gebaseerd op eerdere versies van het dialoogvenster 
      <span class="codeph">zinnen/primetime-sdk-name</span>, waarbij de volumewaarden varieerden van 0 tot 100. </p> </td> 
   </tr> 
   </tbody> 
   </table>
