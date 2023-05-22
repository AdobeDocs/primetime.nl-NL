---
description: TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve mensen de belangen van een publiek vastleggen of negeren.
title: Metingen toevoegen van mat
exl-id: 20962678-15a0-4e7c-96fd-19c59c5ae008
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Metingen toevoegen van mat{#ad-measurements-from-moat}

TVSDK neemt informatie van FreeWheel en andere advertentieservers die VAST-reacties leveren. FreeWheel verstrekt, binnen VAST reacties, informatie van de dienst van de Moat. De Maat-service telt en impressies met een nauwkeurigheid die beter laat zien of creatieve mensen de belangen van een publiek vastleggen of negeren.

Maat is een service voor het meten en weergeven van vele toepassingen, van browsers tot toepassingen. Met de indeling Mat worden in real-time analytische gegevens voor marketingdoeleinden gegenereerd voor verschillende platforms.

De VAST reactie XML heeft een bezit en een element uw code kan lezen, buitenste `Ad id` eigendommen en de buitenwereld `Extension` element. In beide gevallen kan uw code gebruikmaken van TVSDK om beide `Ad id` informatie en `Extension` en ordent de informatie vervolgens in een boomstructuur. Met deze organisatie, kan uw code de gegevens van om het even welk niveau ophalen en het overgaan tot waar het moet gaan. De waarde van de buitenste `Ad id` de eigenschap laat uw code toe om informatie van de bijbehorende campagne te coördineren.

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

Het vastlopen kan ook de `id` eigenschap in de `Ad` -element, zoals in het onderstaande voorbeeld wordt getoond.

```xml
<Ad id="118566" sequence="1">
```

Zie de API-documentatie voor de klasse voor API-informatie [NetworkAdInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/)
