---
description: U kunt meerdere opties voor de bijschriftstijlen opgeven. Deze opties overschrijven de stijlopties in de originele bijschriften.
seo-description: U kunt meerdere opties voor de bijschriftstijlen opgeven. Deze opties overschrijven de stijlopties in de originele bijschriften.
seo-title: Opties voor de stijl van gesloten bijschriften
title: Opties voor de stijl van gesloten bijschriften
uuid: 0e2fd9f3-e569-4b5d-9b78-86f8ee6230ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# Opties voor de stijl van een gesloten bijschrift{#closed-caption-styling-options}

U kunt meerdere opties voor de bijschriftstijlen opgeven. Deze opties overschrijven de stijlopties in de originele bijschriften.

```js
new TextFormat( 
   font,  
   fontColor,  
   edgeColor,  
   fontEdge,  
   backgroundColor,  
   fillColor,  
   size,  
   fontOpacity,  
   backgroundOpacity,  
   fillOpacity, 
   bottomInset, 
   safeArea) 
```

>[!TIP]
>
>In opties die standaardwaarden definiëren (bijvoorbeeld `DEFAULT`), verwijst die waarde naar de instelling op het moment dat de ondertitel oorspronkelijk werd opgegeven.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Indeling </th> 
   <th colname="2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Lettertype </td> 
   <td colname="2"> <p>Het lettertype. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.Font </span> en die bijvoorbeeld een vaste spatiëring met of zonder schreef vertegenwoordigt. </p> <p>Tip:  De werkelijke lettertypen die op een apparaat beschikbaar zijn, kunnen variëren en waar nodig worden vervangende lettertypen gebruikt. Monospace met schreef wordt typisch gebruikt als substituut, hoewel deze substitutie systeemspecifiek kan zijn. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Grootte </td> 
   <td colname="2"> <p>De grootte van het bijschrift. </p> <p> Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.Size </span>: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM  </span> - De standaardgrootte </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROOT  </span> - ongeveer 30% groter dan gemiddeld </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN  </span> - ongeveer 30% kleiner dan gemiddeld </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDAARD  </span> - De standaardgrootte voor het bijschrift; gelijk aan medium </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontkleur </td> 
   <td colname="2"> <p>De fontkleur. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.Color </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Achtergrondkleur </td> 
   <td colname="2"> <p>De kleur van de achtergrondtekencel. </p> <p>Kan alleen worden ingesteld op waarden die beschikbaar zijn voor de lettertypekleur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Dekking van lettertype </td> 
   <td colname="2"> <p>De dekking van de tekst. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY  </span> voor het lettertype is 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Onderste inzet </td> 
   <td colname="2"> <p>De verticale afstand tussen de onderkant van het bijschriftvenster voor bijschriften moet worden vermeden. </p> <p>Wordt uitgedrukt als een percentage van de hoogte van het bijschriftvenster (bijvoorbeeld "20%") of een aantal pixels (bijvoorbeeld "20"). </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Veilig gebied </td> 
   <td colname="2"> <p>Een gebied rond de rand van het scherm tussen 0% en 25% waar bijschriften niet worden weergegeven. </p> <p>Standaard is het veilige gebied voor 608/708 12% en het veilige gebied voor WebVTT 0%. Met deze instelling kan uw toepassing deze standaardinstelling overschrijven. Wanneer twee waarden worden opgegeven, bijvoorbeeld de tekenreeks "10%,20%", is de eerste waarde het horizontale veilige gebied en de tweede waarde het verticale veilige gebied. Wanneer bijvoorbeeld één waarde wordt opgegeven, gebruikt de tekenreeks "15%", zowel de verticale als de horizontale as het opgegeven veilige gebied. </p> </td> 
  </tr> 
 </tbody> 
</table>

