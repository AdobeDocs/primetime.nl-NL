---
description: Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object PTTimedMetadata.
seo-description: Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object PTTimedMetadata.
seo-title: Timed metadata-klasse
title: Timed metadata-klasse
uuid: d1ac6b0b-163f-4968-9160-0f60ff439c09
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Timed metadata-klasse{#timed-metadata-class}

Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object PTTimedMetadata.

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
   <td colname="col1"> <span class="codeph"> metadataId</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span> </td> 
   <td colname="col2"> Unieke id van de metagegevens met tijdslimiet. Deze waarde wordt meestal geëxtraheerd uit het kenmerk cue/tag-id. Anders wordt een unieke willekeurige waarde opgegeven. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"><span class="codeph"> NSString</span></td> 
   <td colname="col2"> De naam van de getimede metagegevens. Als het type <span class="codeph"> TAG</span>is, vertegenwoordigt de waarde de naam van het actiepunt/de tag. Als het type <span class="codeph"> ID3</span>is, is het null. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> tijd</span> </td> 
   <td colname="col02"><span class="codeph"> CMTime</span></td> 
   <td colname="col2"> De tijdpositie, in milliseconden, ten opzichte van het begin van de hoofdinhoud waar deze getimede metagegevens aanwezig zijn in de stream. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> <span class="codeph"> PTTimedMetadataType</span></td> 
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
   >Complexe gegevens in aangepaste tags in het manifest, zoals tekenreeksen met speciale tekens, moeten tussen aanhalingstekens staan. Bijvoorbeeld:   >
   >
   >
   ```>
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```  >
   >



* Als de extractie mislukt vanwege een aangepaste tagindeling, bevat de eigenschap content altijd de onbewerkte gegevens van de tag, de tekenreeks na de dubbele punt. Er wordt in dit geval geen fout gegenereerd.

| Element | Beschrijving |
|---|---|
| TAG, ID3 | Mogelijke typen voor de getimede metagegevens. |
| `@property (nonatomic, assign) CMTime time` | De tijdpositie, relatief ten opzichte van het begin van de hoofdinhoud, waar deze metagegevens in de stream zijn ingevoegd. |
| `@property (nonatomic, assign) PTTimedMetadataType type` | Retourneert het type van de getimede metagegevens. |
| `@property (nonatomic, retain) NSString *metadataId` | Retourneert de id die uit de kenmerken cue/tag is geëxtraheerd. Anders wordt een unieke willekeurige waarde opgegeven. |
| `@property (nonatomic, retain) NSString *name` | Hiermee wordt de naam van de actielijn geretourneerd. Dit is doorgaans de naam van de HLS-tag. |

