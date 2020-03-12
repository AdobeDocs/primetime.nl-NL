---
seo-title: Inhoud leveren
title: Inhoud leveren
uuid: b277d369-fee3-4a20-9dd8-27b3a8a82a9e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Inhoud leveren {#delivering-content}

Primetime DRM is niet op de hoogte van het leveringsmechanisme van de inhoud aangezien runtime de voorzien van een netwerklaag onttrekt en eenvoudig de beschermde inhoud aan het subsysteem Primetime DRM verstrekt. Inhoud kan dus worden geleverd via HTTP, HTTP Dynamic Streaming, RTMP of RTMPE, HLS, enzovoort.

Afhankelijk van het protocol kan het echter lastig zijn om de metagegevens van de beveiligde inhoud op te halen (meestal in de vorm van een `DRMContentData` [!DNL .metadata] bestand dat naast de inhoud wordt geladen). Deze DRM-metagegevens zijn vereist om een willekeurige `DRMManager` API aan te roepen, zoals het vooraf ophalen van de licentie, DRM-verificatie of het aansluiten bij een apparaatdomein. Met het RTMP/RTMPE-protocol kunnen bijvoorbeeld alleen FLV- en F4V-gegevens aan de client worden geleverd via de FMS (Flash Media Server). Daarom moet de client de metagegevensblob op andere manieren ophalen. U kunt dit probleem oplossen door de metagegevens op een HTTP-webserver te hosten en de videospeler van de client te implementeren om de juiste metagegevens op te halen, afhankelijk van de inhoud die wordt afgespeeld.

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

