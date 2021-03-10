---
description: TVSDK biedt u informatie zodat u op doorklikadvertenties kunt werken. Terwijl u de interface van de speler maakt, moet u bepalen hoe u moet reageren wanneer een gebruiker op een klikbare advertentie klikt.
title: Klikbare advertenties
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Klikbare advertenties {#clickable-ads}

TVSDK biedt u informatie zodat u op doorklikadvertenties kunt werken. Terwijl u de interface van de speler maakt, moet u bepalen hoe u moet reageren wanneer een gebruiker op een klikbare advertentie klikt.

Voor TVSDK voor Flash Runtime, slechts zijn de lineaire advertenties klikbaar.

## Reageren op klikken op advertenties {#respond-to-clicks-on-ads}

Wanneer een gebruiker op een advertentie of een verwante knop klikt, is de toepassing verantwoordelijk voor het reageren. TVSDK biedt u informatie over de doel-URL.

In dit voorbeeld ziet u een mogelijke manier om advertenties te beheren.

1. Elke keer dat een advertentie wordt afgespeeld, geeft u een knop boven op de mediaspeler weer. Een gebruiker die op de advertentie klikt, wordt omgeleid naar de advertentie-URL. Deze knop maakt deel uit van [!DNL ClickableAdsOverlay.xml].

   ```xml
      <?xml version="1.0"?> 
   <s:VGroup xmlns:fx="https://ns.adobe.com/mxml/2009"  
       xmlns:s="library://ns.adobe.com/flex/spark" percentWidth="100" horizontalAlign="center">     
           <fx:Declarations><fx:String id="text"/></fx:Declarations> 
           <s:Label text="{text}"  backgroundAlpha="0.75" backgroundColor="#DEDEDE"  
               color="#000000" paddingBottom="5" paddingRight="5" paddingLeft="5"  
               paddingTop="5"/> 
   </s:VGroup>
   ```

1. Neem deze overlay op in ons voorbeeld voor de mediaspeler, [!DNL psdkdemo.xml].

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. Als u de weergave alleen zichtbaar wilt maken wanneer een advertentie wordt afgespeeld, luistert u naar de gebeurtenissen `onAdStart` en `onAdComplete` die door zijn verzonden.

   ```
   _player.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
   _player.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
   ```

   ```
      private function onAdStarted(event:AdPlaybackEvent):void { 
       var primaryAsset:AdAsset = event.ad.primaryAsset; 
       if (primaryAsset.adClick != null) { 
           clickableAdsOverlay.visible = true;  
       } 
   } 
   private function onAdCompleted(event:AdPlaybackEvent):void { 
       clickableAdsOverlay.visible = false; 
   }
   ```

1. Gebruikersinteracties controleren op klikbare advertenties. Wanneer de gebruiker de advertentie of knop aanraakt of erop klikt, geeft u een melding aan TVSDK met `notifyClick`.

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. Luister naar de gebeurtenis `AdclickEvent.AD_CLICK`.

   Als een advertentie wordt afgespeeld, verzendt TVSDK de gebeurtenis `AdClickEvent.AD_CLICK`, waarvan u de doorklikURL en verwante informatie kunt terugwinnen.

   ```
      _player.addEventListener(AdClickEvent.AD_CLICK, onAdClick);
   ```

1. Onderbreek de mediaspeler terwijl de gebruiker naar de advertentie-URL wordt geleid.

   ```
   private function onAdClick(event:AdClickEvent):void { 
       _logger.info("#onAdClick Ad clicked. Target url is {0}", event.adClick.url);  
       _player.pause(); 
       var adRequest:URLRequest = new URLRequest(event.adClick.url); 
       navigateToURL(adRequest, event.adClick.title); 
   }
   ```

1. Geef de URL voor doorklikken en eventuele verwante informatie weer.

       U kunt de presentatie bijvoorbeeld op een van de volgende manieren weergeven:
   
   * Open de doorklikURL in browser binnen uw toepassing.

      Op bureaubladplatforms wordt het video- en afspeelgebied doorgaans gebruikt om doorklikURL&#39;s aan te roepen wanneer de gebruiker klikt.
   * Leid de gebruiker om naar de externe mobiele webbrowser.

      Op mobiele apparaten worden de video en het afspeelgebied gebruikt voor andere functies, zoals het verbergen en weergeven van besturingselementen, het pauzeren van het afspelen, het uitbreiden naar het volledige scherm, enzovoort. Daarom wordt op mobiele apparaten doorgaans een aparte weergave, zoals een sponsor-knop, aan de gebruiker getoond als een manier om de doorklikURL te starten.

1. Sluit het browservenster waarin de doorklikinformatie wordt weergegeven en hervat het afspelen van de video.
