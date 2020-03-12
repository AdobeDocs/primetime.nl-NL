---
description: Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object TimedMetadata.
seo-description: Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object TimedMetadata.
seo-title: Timed metadata-klasse
title: Timed metadata-klasse
uuid: c7b1c1d7-48b3-43c7-aa21-f800d894976d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Timed metadata-klasse {#timed-metadata-class}

Wanneer TVSDK een geabonneerde tag in de afspeellijst/het manifest detecteert, probeert de speler de tag automatisch te verwerken en beschikbaar te maken in de vorm van een object TimedMetadata.

De klasse biedt de volgende elementen:

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b> Eigenschap </b></th> 
   <th colname="col02" class="entry"> <b> Type </b></th> 
   <th colname="col2" class="entry"> <b> Beschrijving </b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> id </span> </td> 
   <td colname="col02"> lang </td> 
   <td colname="col2"> <p>Unieke id van de metagegevens met tijdslimiet. </p> <p>Deze waarde wordt meestal geëxtraheerd uit het kenmerk cue/tag-id. Anders wordt een unieke willekeurige waarde opgegeven. Gebruik <span class="codeph"> getId </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metagegevens </span> </td> 
   <td colname="col02"> Metagegevens </td> 
   <td colname="col2"> <p>De verwerkte/geëxtraheerde informatie uit de aangepaste tag playlist/manifest. Gebruik <span class="codeph"> getMetadata </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> name </span> </td> 
   <td colname="col02"> String </td> 
   <td colname="col2"> <p>De naam van de getimede metagegevens. Als het type <span class="codeph"> </span>TAG is, vertegenwoordigt de waarde de naam van het actiepunt/de tag. Als het type <span class="codeph"> ID3 </span>is, is het null. Gebruik <span class="codeph"> getName </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> tijd </span> </td> 
   <td colname="col02"> lang </td> 
   <td colname="col2"> <p>De tijdpositie, in milliseconden, ten opzichte van het begin van de hoofdinhoud waar deze getimede metagegevens aanwezig zijn in de stream. Gebruik <span class="codeph"> getTime </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> type </span> </td> 
   <td colname="col02"> Type </td> 
   <td colname="col2"> <p>Het type van de getimede meta-gegevens. Gebruik <span class="codeph"> getType </span>. 
     <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
      <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG - geeft aan dat de metagegevens met tijdinstellingen zijn gemaakt op basis van een tag in de afspeellijst/het manifest. </li> 
      <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 - geeft aan dat de metagegevens met tijdinstellingen zijn gemaakt op basis van een ID3-tag in de mediastream. </li> 
     </ul> </p> </td> 
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



* Als de extractie mislukt als gevolg van een aangepaste tagindeling, is de eigenschap metadata leeg en moet de toepassing de werkelijke informatie ophalen. In dit geval wordt geen fout gegenereerd.

<table id="table_1BAE98BF23F641A3A5709EBE37B327F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>Element </b></th> 
   <th colname="col2" class="entry"> <b>Beschrijving</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public enum Type {TAG, ID3} </span> </td> 
   <td colname="col2"> <p>Mogelijke typen voor de getimede metagegevens. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public TimedMetadata(Type, long time, long id, String name, Metadata metadata); </span> </td> 
   <td colname="col2"> <p>Standaardconstructor (time is de lokale streamtijd). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getTime(); </span> </td> 
   <td colname="col2"> <p>De tijdpositie, relatief ten opzichte van het begin van de hoofdinhoud, waar deze metagegevens in de stream zijn ingevoegd. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public Metadata getMetadata(); </span> </td> 
   <td colname="col2"> <p>De metagegevens die in de stream zijn ingevoegd. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public type getType(); </span> </td> 
   <td colname="col2"> <p>Retourneert het type van de getimede metagegevens. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public long getId(); </span> </td> 
   <td colname="col2"> <p>Retourneert de id die uit de kenmerken cue/tag is geëxtraheerd. Anders wordt een unieke willekeurige waarde opgegeven. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public String getName(); </span> </td> 
   <td colname="col2"> <p>Hiermee wordt de naam van de actielijn geretourneerd. Dit is doorgaans de naam van de HLS-tag. </p> </td> 
  </tr> 
 </tbody> 
</table>