---
description: U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.
seo-description: U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.
seo-title: Volumeregeling opgeven
title: Volumeregeling opgeven
uuid: f1e959e0-1817-4ccb-8adc-3eba09c91887
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Volumeregeling opgeven {#provide-volume-control}

U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.

1. In de callback routine voor het interface element van de volumeregelaar, zorg ervoor dat de speler in een geldige status voor dit bevel is.

   >[!TIP]
   >
   >Elke status, behalve RELEASED, is geldig.

1. Bel `setVolume` om het audiovolume in te stellen.

   Bijvoorbeeld:

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   De waarde voor het volume staat voor het gevraagde volume, uitgedrukt als een percentage van het maximale volume, waarbij het stille volume `0` is en het maximale volume `1` is.

