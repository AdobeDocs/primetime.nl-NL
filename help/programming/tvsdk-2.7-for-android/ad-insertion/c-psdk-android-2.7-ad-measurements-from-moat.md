---
description: TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve mensen de belangen van een publiek vastleggen of negeren.
seo-description: TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve mensen de belangen van een publiek vastleggen of negeren.
seo-title: Metingen toevoegen van mat
title: Metingen toevoegen van mat
uuid: b89f900f-50ab-4152-9c0f-11f82d92bffa
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Metingen toevoegen van mat{#ad-measurements-from-moat}

TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve mensen de belangen van een publiek vastleggen of negeren.

Maat is een service voor het meten en weergeven van vele toepassingen, van browsers tot toepassingen. Met de indeling Mat worden in real-time analytische gegevens voor marketingdoeleinden gegenereerd voor verschillende platforms.

De VAST reactie XML heeft een bezit en een element uw code kan lezen, het buitenste `Ad id` bezit en het buitenste `Extension` element. Hoe dan ook, uw code kan TVSDK gebruiken om zowel de `Ad id` informatie als de `Extension` informatie op te slaan en de informatie vervolgens in een boomstructuur te ordenen. Met deze organisatie, kan uw code de gegevens van om het even welk niveau ophalen en het overgaan tot waar het moet gaan. De waarde van het buitenste `Ad id` bezit laat uw code toe om informatie van de bijbehorende campagne te coördineren.

FreeWheel kan bijvoorbeeld gegevens in een Extensions-element retourneren. Hieronder ziet u een voorbeeldelement.

```xml
<?xml version="1.0"?> 
<Extensions> 
  <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
      <MeasurementInfo renditionID="6398737" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions> 
```

Met Freewiel kunt u ook de `id` eigenschap in het `Ad` element instellen, zoals in het onderstaande voorbeeld wordt getoond.

```xml
<Ad id="118566" sequence="1">
```

Zie de API-documentatie voor de klasse [NetworkAndInfo voor API-informatie](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/)
