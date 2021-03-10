---
description: TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve personen de belangen van een publiek vastleggen of negeren.
title: Metingen toevoegen van mat
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# Metingen toevoegen uit moat{#ad-measurements-from-moat}

TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve personen de belangen van een publiek vastleggen of negeren.

Maat is een service voor het meten en weergeven van vele toepassingen, van browsers tot toepassingen. Met de indeling Mat worden in real-time analytische gegevens voor marketingdoeleinden gegenereerd voor verschillende platforms.

De VAST reactie XML heeft een bezit en een element uw code kan lezen, buitenste `Ad id` bezit en buitenste `Extension` element. Hoe dan ook, uw code kan TVSDK gebruiken om zowel de `Ad id` informatie als de `Extension` informatie op te slaan, dan de informatie in een boomstructuur te organiseren. Met deze organisatie, kan uw code de gegevens van om het even welk niveau ophalen en het overgaan tot waar het moet gaan. De waarde van het buitenste `Ad id` bezit laat uw code toe om informatie van de bijbehorende campagne te coördineren.

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

Met Freewiel kunt u ook de eigenschap `id` in het element `Ad` instellen, zoals in het onderstaande voorbeeld wordt getoond.

```xml
<Ad id="118566" sequence="1">
```

Zie de API-documentatie voor de klasse [NetworkAdInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/) voor API-informatie
