---
description: TVSDK neemt informatie van FreeWheel en andere adservers die VAST-reacties verstrekken. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien dat creatieve mensen de belangen van een publiek vastleggen of negeren.
title: Metingen toevoegen van mat
exl-id: 6148268c-8b18-4a94-8209-097d0ae6446b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Metingen toevoegen van mat {#ad-measurements-from-moat}

TVSDK neemt informatie van FreeWheel en andere adservers die VAST-reacties verstrekken. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien dat creatieve mensen de belangen van een publiek vastleggen of negeren.

Maat is een service voor het meten en weergeven van vele toepassingen, van browsers tot toepassingen. Met de indeling Mat worden in real-time analytische gegevens voor marketingdoeleinden gegenereerd voor verschillende platforms.

De VAST reactie XML heeft een bezit en een element uw code kan lezen, het buitenste bezit ad identiteitskaart en het buitenste uitbreidingselement. In beide gevallen kan uw code TVSDK gebruiken om zowel de advertentie-id-informatie als de extensiegegevens op te slaan en de informatie in een boomstructuur te ordenen. Met deze organisatie, kan uw code de gegevens van om het even welk niveau ophalen en het overgaan tot waar het moet gaan. De waarde van het buitenste en identiteitskaart bezit laat uw code toe om informatie van de bijbehorende campagne te coördineren.

FreeWheel kan bijvoorbeeld gegevens in een Extensions-element retourneren. Hieronder ziet u een voorbeeldelement.

```xml
<Extensions> 
   <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
     <MeasurementInfo renditionID="6398737" type="MediaFile"> 
      <MoatID> 
       <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
       <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID> 
        <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
        <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions>
```

Met Freewiel kunt u ook de id-eigenschap instellen in het element Advertentie, zoals in het onderstaande voorbeeld wordt getoond.

```
<Ad id="118566" sequence="1">
```

Raadpleeg de API-documentatie voor de klasse `PTNetworkAdInfo` in `PTAdAsset`.
