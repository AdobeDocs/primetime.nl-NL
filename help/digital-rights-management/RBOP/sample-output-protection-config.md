---
description: Deze sectie stelt een steekproefconfiguratie voor die de concepten en de vorm van de configuratie illustreert.
title: Voorbeeld van RBOP-configuratie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# Voorbeeld van RBOP-configuratie {#sample-rbop-configuration}

Deze sectie stelt een steekproefconfiguratie voor die de concepten en de vorm van de configuratie illustreert.

De volgende voorbeeld-JSON-configuratie definieert een pixeluitvoerbeleid dat het volgende opgeeft:

* Decodering van de video beperken tot resoluties van 1080 of lager
* Stel specifieke beperkingen op voor resoluties 720 en 480:

   * Voor resolutie 720: HDCP vereist voor digitale uitvoer; vereist *Generation Management System kopiëren - Analog* (CGMS-A) bescherming voor analoge uitvoer.
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

* De `pixelCount` specificaties zijn één niveau lager in de JSON-structuur, binnen de sectie `pixelConstraints`.

* Binnen elke specificatie voor pixelaantallen is uitvoerbeveiliging opgegeven voor zowel digitale als analoge uitvoer.
* In de specificaties voor digitale uitvoer worden HDCP-versies opgegeven, hoewel de client momenteel geen HDCP-versioning ondersteunt. Raadpleeg de veelgestelde vragen voor meer informatie.

