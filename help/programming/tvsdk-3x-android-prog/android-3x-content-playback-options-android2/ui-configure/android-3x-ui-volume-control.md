---
description: U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.
seo-description: U kunt opstelling een controle van de gebruikersinterface om het volume voor de video aan te passen.
seo-title: Volumeregeling opgeven
title: Volumeregeling opgeven
uuid: c87fe656-0329-4c9c-b65b-43be48c77062
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

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