---
description: Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object TimedMetadata.
seo-description: Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object TimedMetadata.
seo-title: Timed metadata-klasse
title: Timed metadata-klasse
uuid: 827a3bcf-a584-4032-aa19-4fc7730778cc
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Timed metadata-klasse{#timed-metadata-class}

Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object TimedMetadata.

De klasse biedt de volgende elementen:

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Eigenschap </th> 
   <th colname="col02" class="entry"> Type </th> 
   <th colname="col2" class="entry"> Beschrijving </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> content</span> </td> 
   <td colname="col02"> String </td> 
   <td colname="col2"> De onbewerkte inhoud van de getimede metagegevens. Als het type TAG is, vertegenwoordigt de waarde de volledige kenmerklijst van de cue/tag. Als het type id ID3, het ongeldig is. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> id</span> </td> 
   <td colname="col02"> String </td> 
   <td colname="col2"> Unieke id van de metagegevens met tijdslimiet. Deze waarde wordt meestal geëxtraheerd uit het kenmerk cue/tag-id. Anders wordt een unieke willekeurige waarde opgegeven. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> metagegevens</span> </td> 
   <td colname="col02"> Metagegevens </td> 
   <td colname="col2"> De verwerkte/geëxtraheerde informatie uit de aangepaste tag playlist/manifest. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"> String </td> 
   <td colname="col2">De naam van de getimede metagegevens. Als het type <span class="codeph"> TAG</span>is, vertegenwoordigt de waarde de naam van het actiepunt/de tag. Als het type <span class="codeph"> ID3</span>is, is het null. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> tijd</span> </td> 
   <td colname="col02"> Getal </td> 
   <td colname="col2"> De tijdpositie, in milliseconden, ten opzichte van het begin van de hoofdinhoud waar deze getimede metagegevens aanwezig zijn in de stream. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> String </td> 
   <td colname="col2">Het type van de getimede meta-gegevens. 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG - geeft aan dat de metagegevens met tijdinstellingen zijn gemaakt op basis van een tag in de afspeellijst/het manifest. </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 - geeft aan dat de metagegevens met tijdinstellingen zijn gemaakt op basis van een ID3-tag in de mediastream. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

Houd rekening met het volgende:

* TVSDK extraheert de lijst met kenmerken automatisch naar sleutelwaardeparen en slaat de kenmerken op in de eigenschap metadata.

   >[!TIP]
   >
   >Complexe gegevens in aangepaste tags in het manifest, zoals tekenreeksen met speciale tekens, moeten tussen aanhalingstekens staan. Bijvoorbeeld:
   >
   >
   ```
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* Als de extractie mislukt als gevolg van een aangepaste tagindeling, is de eigenschap metadata leeg en moet de toepassing de werkelijke informatie ophalen. Er wordt in dit geval geen fout gegenereerd.

| Element | Beschrijving |
|---|---|
| `TAG, ID3 ID3, TAG` | Mogelijke typen voor de getimede metagegevens. |
| `public function TimedMetadata(type:String, time:Number, id:String, name:String, content:String, metadata:Metadata)` | Standaardconstructor (time is de lokale streamtijd). |
| `content:String` | De onbewerkte inhoud van de brontag van deze getimede metagegevens. |
| `time:Number` | De tijdpositie, relatief ten opzichte van het begin van de hoofdinhoud, waar deze metagegevens in de stream zijn ingevoegd. |
| `metadata:Metadata` | De metagegevens die in de stream zijn ingevoegd. |
| `type:String` | Retourneert het type van de getimede metagegevens. |
| `id:String` | Retourneert de id die uit de kenmerken cue/tag is geëxtraheerd. Anders wordt een unieke willekeurige waarde opgegeven. |
| `name:String` | Hiermee wordt de naam van de actielijn geretourneerd. Dit is doorgaans de naam van de HLS-tag. |

