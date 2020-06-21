---
description: Veelgestelde vragen over het gebruik van op resolutie gebaseerde outputbescherming.
seo-description: Veelgestelde vragen over het gebruik van op resolutie gebaseerde outputbescherming.
seo-title: Veelgestelde vragen over RBOP
title: Veelgestelde vragen over RBOP
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Veelgestelde vragen over RBOP {#rbop-faq}

Veelgestelde vragen over het gebruik van op resolutie gebaseerde outputbescherming.

* **V.** *Wanneer het bepalen van een digitale outputvereiste voor een pixelbeperking, krijg ik ontleed/formatterende fouten wanneer ik de versie van HDCP uit verlaat, maar ik heb geen vereisten HDCP. Hoe zou ik mijn digitale outputvereiste in dit geval moeten vormen?* **A.** Aangezien controle van de HDCP-versie momenteel niet wordt ondersteund op de client, raadt Adobe aan de HDCP-versie in te stellen op `1.0`. Zo weet u zeker dat uw configuratie correct is opgemaakt en in de toekomst semantisch consistent is wanneer controle van de HDCP-versie wordt ondersteund. Het volgende fragment illustreert een configuratie met deze HDCP-waarde.

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

   * 240, 480: beide zijn &lt;= 480; er is geen OP vereist en stromen worden geladen met of zonder HDCP.
   * 600, 720: beide zijn &lt;= 720; HDCP is vereist voor afspelen
   * 1080: > 720; de stream wordt in een bloklijst weergegeven (fout wordt geretourneerd) omdat deze niet wordt gevonden in de bovenstaande regels.


* **V.** Op sommige van mijn Android-apparaten worden de door mij gedefinieerde beperkingen voor het aantal pixels niet precies zo toegepast als gedefinieerd. Wat gebeurt er?

   **A.** Sommige Android-apparaten melden een framegrootte die iets groter is dan de normale grootte. U kunt deze situatie verhelpen door de framegrootten ( `maxPixel` en `pixelCount` instellingen) met 20 pixels naar boven aan te passen. Pas bijvoorbeeld de instellingen voor de framegrootte naar boven aan, van:

   ```
   { 
       "maxPixel":  
   
<b>800</b>,&quot;pixelConstraints&quot;: [{ &quot;pixelCount&quot;:\
<b>532</b>,&quot;digitaal&quot;: [{&quot;uitvoer&quot;: &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;: 1,&quot;minderjarig&quot;: 0}}],&quot;analoog&quot;: {&quot;uitvoer&quot;: &quot;REQUIRED&quot;},...

```
to: 
```
{1} &quot;maxPixel&quot;:\
<b>820</b>,&quot;pixelConstraints&quot;: [{ &quot;pixelCount&quot;:\
<b>552</b>,&quot;digitaal&quot;: [{&quot;uitvoer&quot;: &quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;: 1,&quot;minderjarig&quot;: 0}}],&quot;analoog&quot;: {&quot;uitvoer&quot;: &quot;REQUIRED&quot;},...

```
throughout, for all instances of `maxPixel` and `pixelCount`.

