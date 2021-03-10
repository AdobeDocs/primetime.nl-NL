---
description: U kunt een gebruikersinterfacecontrole instellen om het volume voor de video aan te passen.
title: Volumeregeling opgeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 2%

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

