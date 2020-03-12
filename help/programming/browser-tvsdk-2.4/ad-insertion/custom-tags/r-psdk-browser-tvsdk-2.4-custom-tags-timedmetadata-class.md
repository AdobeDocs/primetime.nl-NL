---
description: Wanneer Browser TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken als een object TimedMetadata.
seo-description: Wanneer Browser TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken als een object TimedMetadata.
seo-title: Timed metadata-klasse
title: Timed metadata-klasse
uuid: 3f276618-5f61-4b41-bd2d-78e7f32178d9
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Timed metadata-klasse{#timed-metadata-class}

Wanneer Browser TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken als een object TimedMetadata.

De `TimedMetadata` klasse biedt de volgende elementen:

<table id="table_5827A0626EDC45F68DC3E7644F3EFF69"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Eigenschap </th> 
   <th colname="col02" class="entry"> Type </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>type </p> </td> 
   <td colname="col02"> <p><span class="codeph"> TimedMetadataType</span> </p> </td> 
   <td colname="col2"> <p>Hier volgen de metagegevenstypen met tijdslimiet: 
     <ul id="ul_E79C375A54C64BF09A927EE8983E98E3"> 
      <li id="li_F1907521CDBE47E282A87AF0A7A1477A">TAG - de getimede metagegevens zijn gemaakt op basis van een tag in de afspeellijst/manifest. </li> 
      <li id="li_5B0C0B0F247144709F86E6654A5AB500">ID3 - de getimede metagegevens zijn gemaakt op basis van een ID3-tag in de mediastream. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>tijd </p> </td> 
   <td colname="col02"> <p>Getal </p> </td> 
   <td colname="col2"> <p>De lokale tijdpositie (milliseconden) ten opzichte van het begin van de hoofdinhoud, waarbij deze metagegevens met tijdslimiet in de stream aanwezig zijn. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>id </p> </td> 
   <td colname="col02"> <p>String </p> </td> 
   <td colname="col2"> <p>De unieke id van de getimede metagegevens. </p> <p>Wordt meestal geëxtraheerd uit het kenmerk cue/tag-id, indien aanwezig. Anders is het een unieke willekeurige waarde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>name </p> </td> 
   <td colname="col02"> <p>Getal </p> </td> 
   <td colname="col2"> <p>De naam van de getimede metagegevens. </p> <p>Als het type TAG is, vertegenwoordigt de waarde de naam van het actiepunt/de tag. Als het type ID3 is, is de waarde null. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>content </p> </td> 
   <td colname="col02"> <p>String </p> </td> 
   <td colname="col2"> <p>De onbewerkte inhoud van de getimede metagegevens. </p> <p>Als het type TAG is, vertegenwoordigt de waarde de volledige kenmerklijst van de cue/tag. Als het type id ID3, is de waarde null. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>metagegevens </p> </td> 
   <td colname="col02"> <p><span class="codeph"> Metagegevens</span> </p> </td> 
   <td colname="col2"> <p>De verwerkte/geëxtraheerde informatie uit de aangepaste tag playlist/manifest. </p> </td> 
  </tr> 
 </tbody> 
</table>

