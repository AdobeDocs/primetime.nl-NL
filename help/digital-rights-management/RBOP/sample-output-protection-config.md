---
description: Deze sectie stelt een steekproefconfiguratie voor die de concepten en de vorm van de configuratie illustreert.
title: Voorbeeld van RBOP-configuratie
exl-id: 0f40be83-9c7f-482b-ac42-9aa4e3f46f58
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Voorbeeld van RBOP-configuratie {#sample-rbop-configuration}

Deze sectie stelt een steekproefconfiguratie voor die de concepten en de vorm van de configuratie illustreert.

De volgende voorbeeld-JSON-configuratie definieert een pixeluitvoerbeleid dat het volgende opgeeft:

* Decodering van de video beperken tot resoluties van 1080 of lager
* Stel specifieke beperkingen op voor resoluties 720 en 480:

   * Voor resolutie 720: HDCP vereist voor digitale uitvoer; vereisen *Generatiebeheersysteem kopiëren - analoog* (CGMS-A) bescherming voor analoge uitvoer.
   * Voor resolutie 480: HDCP vereist voor digitale uitvoer; geen bescherming van het analoge

```
{ 
  "pixelConstraints":  
    [ 
      { 
        "pixelCount": 720, 
        "digital": 
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "REQUIRED_CGMSA"} 
      }, 
      { 
        "pixelCount": 480, 
        "digital":  
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "NO_PROTECTION"} 
      } 
    ], 
  "maxPixel": 1080 
}
```

Neem nota van het volgende over de steekproefconfiguratie hierboven:

* De `pixelCount` de specificaties zijn één niveau lager in de JSON-structuur, binnen de `pixelConstraints` sectie.

* Binnen elke specificatie voor pixelaantallen is uitvoerbeveiliging opgegeven voor zowel digitale als analoge uitvoer.
* In de specificaties voor digitale uitvoer worden HDCP-versies opgegeven, hoewel de client momenteel geen HDCP-versioning ondersteunt. Raadpleeg de veelgestelde vragen voor meer informatie.
