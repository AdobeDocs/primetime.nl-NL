---
description: U kunt een gebruikersinterfacecontrole instellen om het volume voor de video aan te passen.
title: Volumeregeling opgeven
exl-id: 0daa87e2-51aa-4459-9a67-135dc54d09c7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Volumeregeling opgeven {#provide-volume-control}

U kunt een gebruikersinterfacecontrole instellen om het volume voor de video aan te passen.

1. In de callback routine voor het interface element van de volumeregelaar, zorg ervoor dat de speler in een geldige status voor dit bevel is.

   >[!TIP]
   >
   >Elke status, behalve RELEASED, is geldig.

1. Bellen `setVolume` om het audiovolume in te stellen.

   Bijvoorbeeld:

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   De waarde van het volume staat voor het gevraagde volume, uitgedrukt als een percentage van het maximumvolume, waarbij `0` is stil en `1` is het maximale volume.
