---
description: U kunt een gebruikersinterfacecontrole instellen om het volume voor de video aan te passen.
seo-description: U kunt een gebruikersinterfacecontrole instellen om het volume voor de video aan te passen.
seo-title: Volumeregeling opgeven
title: Volumeregeling opgeven
uuid: c87fe656-0329-4c9c-b65b-43be48c77062
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# Verstrek volumeregeling {#provide-volume-control}

U kunt een gebruikersinterfacecontrole instellen om het volume voor de video aan te passen.

1. In de callback routine voor het interface element van de volumeregelaar, zorg ervoor dat de speler in een geldige status voor dit bevel is.

   >[!TIP]
   >
   >Elke status, behalve RELEASED, is geldig.

1. Roep `setVolume` aan om het audiovolume in te stellen.

   Bijvoorbeeld:

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   De waarde voor het volume vertegenwoordigt het gevraagde volume uitgedrukt als een percentage van het maximale volume, waarbij `0` stil is en `1` het maximale volume is.