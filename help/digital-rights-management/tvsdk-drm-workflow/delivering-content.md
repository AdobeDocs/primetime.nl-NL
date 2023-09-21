---
title: Inhoud leveren
description: Inhoud leveren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Inhoud leveren {#delivering-content}

Primetime DRM is niet op de hoogte van het leveringsmechanisme van de inhoud aangezien runtime de voorzien van een netwerklaag onttrekt en eenvoudig de beschermde inhoud aan het subsysteem Primetime DRM verstrekt. Inhoud kan dus worden geleverd via HTTP, HTTP Dynamic Streaming, RTMP of RTMPE, HLS, enzovoort.

Afhankelijk van het protocol kunnen er echter problemen optreden bij het ophalen van de metagegevens van de beveiligde inhoud ( `DRMContentData` - gewoonlijk in de vorm van een zijdelings geladen [!DNL .metadata] bestand). Deze DRM-metagegevens zijn vereist voor het aanroepen van `DRMManager` API, zoals het vooraf ophalen van de licentie, DRM-verificatie of het aansluiten bij een apparaatdomein. Met het RTMP/RTMPE-protocol kunnen bijvoorbeeld alleen FLV- en F4V-gegevens via de Flash Media Server (FMS) aan de client worden geleverd. Daarom moet de client de metagegevensblob op andere manieren ophalen. U kunt dit probleem oplossen door de metagegevens op een HTTP-webserver te hosten en de videospeler van de client te implementeren om de juiste metagegevens op te halen, afhankelijk van de inhoud die wordt afgespeeld.

```
private function getMetadata():void { 
    extrapolated-path-to-metadata = "https://metadatas.mywebserver.com/" + videoname; 
     var urlRequest : URLRequest =  
      new URLRequest(extrapolated-path-to-the-metadata + ".metadata");  
    var urlStream : URLStream = new URLStream();  
    urlStream.addEventListener(Event.COMPLETE, handleMetadata);  
    urlStream.addEventListener(IOErrorEvent.NETWORK_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.IO_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.VERIFY_ERROR, handleIOError);  
 
    try { 
        urlStream.load(urlRequest);  
    } catch(se:SecurityError) { 
        videoLog.text += se.toString() + "\n";  
    } catch(e:Error) { 
        videoLog.text += e.toString() + "\n";  
    } 
} 
```
