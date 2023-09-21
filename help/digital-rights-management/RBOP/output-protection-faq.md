---
description: Veelgestelde vragen over het gebruik van op resolutie gebaseerde outputbescherming.
title: Veelgestelde vragen over RBOP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Veelgestelde vragen over RBOP {#rbop-faq}

Veelgestelde vragen over het gebruik van op resolutie gebaseerde outputbescherming.

* **V.** *Wanneer het bepalen van een digitale outputvereiste voor een pixelbeperking, krijg ik ontleed/formatterende fouten wanneer ik de versie van HDCP uit verlaat, maar ik heb geen vereisten HDCP. Hoe zou ik mijn digitale outputvereiste in dit geval moeten vormen?* **A.** Aangezien controle van de HDCP-versie momenteel niet wordt ondersteund op de client, wordt het aanbevolen de HDCP-versie in te stellen op `1.0`. Zo weet u zeker dat uw configuratie correct is opgemaakt en in de toekomst semantisch consistent is wanneer controle van de HDCP-versie wordt ondersteund. Het volgende fragment illustreert een configuratie met deze HDCP-waarde.

  ```
  { "pixelConstraints":  
    [  
      { "pixelCount": 720, "digital":  
        [  
          {  
            "output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}  
          }  
        ]  
      }  
    ]  
  }
  ```

* **V.** *Zijn RBOP pixelbeperkingen discreet of gebaseerd op bereik?* **A.** RBOP-pixelbeperkingen zijn gebaseerd op bereik. Elk aantal pixels definieert de vereisten voor alle aantal pixels dat kleiner is dan of gelijk is aan het opgegeven aantal of tot het hoogste aantal dat kleiner is dan die waarde als er meer dan één pixelbeperking bestaat. Eenvoudig gesteld, zijn de waarden als maximumdrempels voor elke verticale pixeltelling van toepassing.

  Stel dat een MBR-stroom met verticale resoluties van 240, 480, 600, 720 en 1080 aan de speler wordt doorgegeven met de volgende RBOP-instellingen.

  **RBOP-beleidsinstellingen:**

   * 720P - HDCP vereist
   * 480P - Geen OP

  Op elke variant worden de volgende regels toegepast.

  **Streams:**

   * 240, 480: Beide zijn &lt;= 480; geen OP is vereist en stromen worden geladen met of zonder HDCP.
   * 600, 720: Beide zijn &lt;= 720; HDCP is vereist voor afspelen
   * 1080: > 720; de stream wordt in de bloklijst weergegeven (fout wordt geretourneerd) omdat deze niet wordt gevonden in de bovenstaande regels.

* **V.** Op sommige van mijn Android-apparaten worden de door mij gedefinieerde beperkingen voor het aantal pixels niet precies zo toegepast als gedefinieerd. Wat gebeurt er?

  **A.** Sommige Android-apparaten melden een framegrootte die iets groter is dan de normale grootte. U kunt deze situatie verhelpen door de framegrootten aan te passen ( `maxPixel` en `pixelCount` (instellingen) met 20 pixels naar boven. Pas bijvoorbeeld de instellingen voor de framegrootte naar boven aan, van:

  ```
  { 
      "maxPixel": 800, 
      "pixelConstraints": [ 
          { "pixelCount": 532, 
            "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
            "analog": {"output": "REQUIRED"} 
          }, 
  ... 
  ```

  tot:

  ```
  { 
      "maxPixel": 820, 
      "pixelConstraints": [ 
          { "pixelCount": 552, 
            "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
            "analog": {"output": "REQUIRED"} 
          }, 
  ... 
  ```

  voor alle gevallen van `maxPixel` en `pixelCount`.
