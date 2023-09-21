---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumecontrole bieden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Volumecontrole bieden{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht tot de instantie MediaPlayer in een geldige staat voor dit bevel is, dat om het even welk behalve RELEASED of FOUT is.
1. Bellen `setVolume` op de `MediaPlayer` -instantie om het audiovolume in te stellen.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   De waarde voor het volume geeft het gevraagde volume weer, uitgedrukt in verhouding tot het maximale volume, waarbij 0 stil is en 100 het maximale volume.
