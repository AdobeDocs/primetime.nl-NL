---
description: U kunt om het even welke stromen van een op TVSDK-Gebaseerde afzenderapp gieten en de stroom hebben teruggespeeld op Chromecast met Browser TVSDK.
seo-description: U kunt om het even welke stromen van een op TVSDK-Gebaseerde afzenderapp gieten en de stroom hebben teruggespeeld op Chromecast met Browser TVSDK.
seo-title: Google Cast-app voor TVSDK van browser
title: Google Cast-app voor TVSDK van browser
uuid: 018143e2-143a-4f88-97c6-4b10a2083f9e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Google Cast-app voor TVSDK van browser{#google-cast-app-for-browser-tvsdk}

U kunt om het even welke stromen van een op TVSDK-Gebaseerde afzenderapp gieten en de stroom hebben teruggespeeld op Chromecast met Browser TVSDK.

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Er zijn twee componenten van een app voor Cast:

* De afzender-app, die fungeert als de afstandsbediening.

   Toepassingen van de afzender omvatten smartphones, pc&#39;s enzovoort. De app kan worden ontwikkeld met behulp van native SDK&#39;s voor iOS, Android en Chrome.
* De ontvanger-app, die op Chromecast wordt uitgevoerd en de inhoud afspeelt.

   >[!IMPORTANT]
   >
   >Deze app kan alleen een HTML5-app zijn.

De afzender en de ontvanger communiceren door de Gegoten SDKs te gebruiken om berichten over te gaan.

## Standaardworkflow {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

Hier volgt een overzicht van het proces:

1. De afzender-app maakt een verbinding met de ontvanger-app.
1. De afzender-app verzendt een bericht om de media in de ontvanger-app te laden.
1. De ontvanger-app begint het afspelen.
1. De afzenderapp stuurt afspeelbesturingsberichten, zoals afspelen, pauzeren, zoeken, vooruitspoelen, snel terugspoelen, terugspoelen, volumewijziging enzovoort, naar de ontvanger-app.
1. De ontvanger-app reageert op deze berichten.

## Berichtformaat {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

U moet de berichten bepalen zodat de afzender en de ontvanger kunnen begrijpen. Hier volgt een voorbeeld van een zoekbericht:

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

Wanneer het verzenden van douaneberichten zoals het zoekbericht door de Gegoten SDKs, wordt een douanebericht namespace vereist. Hier volgt een voorbeeld in JavaScript:

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## Verbinding {#section_B4D40CABDD3E46FDBE7B5651DFF91653} maken

>[!IMPORTANT]
>
>De browser TVSDK APIs zijn niet betrokken wanneer het vestigen van de verbinding.

Om een verbinding tot stand te brengen, moeten de afzender en de ontvanger de volgende taken voltooien:

* De afzender moet de documentatie voor platform op [Sender App Development](https://developers.google.com/cast/docs/sender_apps) herzien.
* De ontvanger gebruikt de ontvanger APIs van de Gietvorm om een verbinding met de afzender te vestigen app. Bijvoorbeeld:

   ```js
   window.castReceiverManager = cast.receiver.CastReceiverManager.getInstance(); 
   
   window.castReceiverManager.onReady = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderConnected = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderDisconnected = function (event) { /*handle event*/ }; 
   
   var customMessageBus = window.castReceiverManager.getCastMessageBus(MSG_NAMESPACE); 
   customMessageBus.onMessage = function (event) { /*handle messages*/ }; 
   
   window.castReceiverManager.start(); 
   ```

## Berichtverwerking {#section_3E4814546F5946C9B3E7A1AE384B4FF8}

Om berichten naar de ontvanger te verzenden, zie de documentatie voor het platform van uw afzender.

>[!IMPORTANT]
>
>U moet de naamruimte van het aangepaste bericht `MSG_NAMESPACE` in alle berichten opnemen.

Voor de ontvanger app, volg de documentatie voor de gietvormontvanger APIs.

**Voorbeeld van een Chrome-Gebaseerd Bericht van de Afzender**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Gebeurtenisafhandeling van op chroom gebaseerde afzender**

Bind gebeurtenismanagers aan uw elementen UI die berichten zullen verzenden wanneer de overeenkomstige gebeurtenissen worden teweeggebracht. Voor een Chrome-gebaseerde afzender-app kan de zoekgebeurtenis bijvoorbeeld als volgt worden verzonden:

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**Ontvangersberichten verwerken**

In de ontvanger-app ziet u een voorbeeld van hoe u het zoekbericht kunt afhandelen:

```js
customMessageBus.onMessage = function (event) { 
    var message = JSON.parse(event.data); 
    switch (message.type) { 
        case "seek":  
            player.seek(parseInt(message.seekTo)); 
            break; 
        //code for handling other events 
        default:  
            break; 
    } 
}; 
```

