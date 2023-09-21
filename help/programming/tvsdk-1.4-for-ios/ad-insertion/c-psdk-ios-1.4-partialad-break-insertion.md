---
description: TVSDK biedt een tv-achtige ervaring om in live streams deel te kunnen nemen aan een advertentie.
title: Gedeeltelijke invoeging ad-break
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Gedeeltelijke invoeging ad-break{#partial-ad-break-insertion}

TVSDK biedt een tv-achtige ervaring om in live streams deel te kunnen nemen aan een advertentie.

Met de gedeeltelijke invoegfunctie ad-break kunt u een tv-achtige ervaring nabootsen waarbij, als de client een live stream start in een mid-roll, deze begint met afspelen binnen die mid-roll. Het is vergelijkbaar met het schakelen naar een tv-zender en de reclames werken naadloos.

Als een gebruiker zich bijvoorbeeld in het midden van een 90 seconden bij het afbreken aanmeldt (drie 30 seconden bij advertenties), 10 seconden bij de tweede advertentie (dat wil zeggen, bij 40 seconden bij het afspelen), wordt de tweede advertentie afgespeeld voor de resterende duur (20 seconden) gevolgd door de derde advertentie.

## Advertentie bijhouden {#section_03AFAEAA8DA44399952DC51C5E12951E}

Er worden geen trackers voor de gedeeltelijk afgespeelde advertentie (de tweede advertentie) geactiveerd. In het bovenstaande voorbeeld wordt alleen de tracker voor de derde advertentie geactiveerd.

## Gedrag met voorrol {#section_7DFBFB12E63343D1A0C614F0CF9F1714}

De functie werkt wanneer een pre-roll advertentie met levende inhoud wordt gespeeld. De stream wordt vanaf het actieve punt afgespeeld nadat de pre-roll-advertentie is beëindigd.

Gebeurtenissen voor een regeleinde worden verzonden, zelfs als er geen volledige advertenties in dit advertentie-einde staan. Een advertentie wordt als gedeeltelijke advertentie beschouwd, als deze gedurende meer dan één seconde wordt overgeslagen. Als een viewer bijvoorbeeld een advertentie kijkt die ze 800 ms hebben overgeslagen, wordt deze beschouwd als een complete advertentie.
