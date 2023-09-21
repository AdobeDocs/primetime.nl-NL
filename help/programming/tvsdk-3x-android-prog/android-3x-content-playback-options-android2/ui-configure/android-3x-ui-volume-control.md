---
description: U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.
title: Volumecontrole bieden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Volumecontrole bieden {#provide-volume-control}

U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.

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
