---
description: ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. Browser TVSDK ontdekt ID3 markeringen op het het segmentniveau van de vervoerstroom (TS) in HLS stromen en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.
seo-description: ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. Browser TVSDK ontdekt ID3 markeringen op het het segmentniveau van de vervoerstroom (TS) in HLS stromen en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.
seo-title: ID3-tags
title: ID3-tags
uuid: a47cd0cc-b11d-47df-b1fb-56918896ef4c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# ID3-tags{#id-tags}

ID3-tags bieden informatie over een audio- of videobestand, zoals de titel van het bestand of de naam van de artiest. Browser TVSDK ontdekt ID3 markeringen op het het segmentniveau van de vervoerstroom (TS) in HLS stromen en verzendt een gebeurtenis. De toepassing kan gegevens uit de tag extraheren.

Wanneer een nieuwe ID3-metagegevens wordt gevonden in de onderliggende HLS-stream, activeert Browser-TVSDK een `AdobePSDK.TimedMetadataEvent`-gebeurtenis.

Het object `TimedMetadata` voor ID3 heeft de volgende eigenschappen:

<table id="table_6C61886187FB44B4B9821E4B00200018"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Eigenschapnaam </th> 
   <th colname="col2" class="entry"> Details </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> type  </span> </p> </td> 
   <td colname="col2"> <p>Een type van <span class="codeph"> TimedMetadata </span> voorwerp. </p> <p>Voor ID3-metagegevens is de waarde <span class="codeph"> AdobePSDK.TimedMetadataType.ID3 </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> tijd  </span> </p> </td> 
   <td colname="col2"> <p> De spelertijd waar deze getimede meta-gegevens werd ontdekt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id  </span> </p> </td> 
   <td colname="col2"> <p>Id van <span class="codeph"> TimedMetadata </span>-object. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> name </span> </p> </td> 
   <td colname="col2"> <p>Naam van object <span class="codeph"> TimedMetadata </span>. Voor ID3-metagegevens is de waarde "ID3". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> content  </span> </p> </td> 
   <td colname="col2"> <p>De inhoud van getimede metagegevens. Voor ID3-tags vertegenwoordigt deze waarde de geserialiseerde bytearray. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> metagegevens  </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> TimedMetadata  </span> processing information, wat een geval van  <span class="codeph"> AdobePSDK.Metadata is  </span> waar de ID3 kaders worden opgeslagen. </p> <p> <p>Opmerking:  Voor Safari <span class="codeph">-video </span>-tags worden de specifieke framegegevens van de ID3-tag in de vorm van een object weergegeven via een <span class="codeph"> AdobePSDK.Metadata </span>-object, terwijl voor andere browsers de framegegevens van de ID3-tag worden weergegeven in de vorm van een bytearray via een <span class="codeph"> AdobePSDK.Metadata </span>-object. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

&#x200B;

De verschillende ID3-tags die zijn opgeslagen in `TimedMetadata` kunnen door de toepassing op de volgende twee manieren worden opgehaald:

* In de gebeurtenislistener AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE.

   ```
   var isSafari = function () { 
       var nAgt = navigator.userAgent; 
       var appName = navigator.appName; 
       if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
           (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
           (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
           (nAgt.indexOf('Chrome') === -1) && // is not chrome 
           (nAgt.indexOf('Safari') !== -1) //is Safari 
       ){ 
           return true; 
       } 
       return false; 
   }; 
   var hex2a = function (hex, offset, max) { 
       var str = ''; 
       if (!hex) 
           return str; 
       for (var i = offset; i < hex.length && i < offset + max; i++) 
           str += String.fromCharCode(hex[i]); 
       return str; 
   }; 
   var mediaPlayer = new AdobePSDK.MediaPlayer(); 
   mediaPlayer.addEventListener( AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE ,function(event){ 
       var td = event.timedMetadata; 
       if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
           var md = td.metadata; 
           var keySet = md.keySet; 
           var onSafari = isSafari(); 
           if(keySet && keySet.length){ 
               var msg = ''; 
               for(var j = 0; j < keySet.length; j++){ 
                   var idTag = keySet[j]; 
                   msg += idTag; 
                   if(idTag.indexOf("T") == 0){ 
                       /* text frame*/ 
                       if(onSafari){ 
                           /* text frame data is exposed in object format 
                            * where corresponding text data is exposed through 
                            * data key of text frame data object 
                            * */ 
                           var frameDataObject = md.getObject(idTag); 
                           msg += " : " + frameDataObject.data; 
                       } else { 
                           var buff = md.getByteArray(idTag); 
                           msg += " : " + hex2a(buff, 0, buff.length - 1); 
                       } 
                   } 
                   msg += " ; "; 
               } 
           } 
       } 
   }); 
   ```

* De `MediaPlayerItem`-eigenschap `timedMetadata` gebruiken.

   ```
   var isSafari = function () { 
       var nAgt = navigator.userAgent; 
       var appName = navigator.appName; 
       if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
           (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
           (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
           (nAgt.indexOf('Chrome') === -1) && // is not chrome 
           (nAgt.indexOf('Safari') !== -1) //is Safari 
       ){ 
           return true; 
       } 
       return false; 
   }; 
   var hex2a = function (hex, offset, max) { 
       var str = ''; 
       if (!hex) 
           return str; 
       for (var i = offset; i < hex.length && i < offset + max; i++) 
           str += String.fromCharCode(hex[i]); 
       return str; 
   }; 
   var timedMetadataList = player.currentItem.timedMetadata; 
   for(var i = 0; i < timedMetadataList.length; i++){ 
       var td = timedMetadataList[i]; 
       if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
           var md = td.metadata; 
           var keySet = md.keySet; 
           var onSafari = isSafari(); 
           if(keySet && keySet.length){ 
               var msg = ''; 
               for(var j = 0; j < keySet.length; j++){ 
                   var idTag = keySet[j]; 
                   msg += idTag; 
                   if(idTag.indexOf("T") == 0){ 
                       /* text frame*/ 
                       if(onSafari){ 
                           /* text frame data is exposed in object format 
                            * where corresponding text data is exposed through 
                            * data key of text frame data object 
                            * */ 
                           var frameDataObject = md.getObject(idTag); 
                           msg += " : " + frameDataObject.data; 
                       } else { 
                           var buff = md.getByteArray(idTag); 
                           msg += " : " + hex2a(buff, 0, buff.length - 1); 
                       } 
                   } 
                   msg += " ; "; 
               } 
           } 
       } 
   } 
   ```

