---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumeregeling opgeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Verstrek volumeregeling{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht tot de instantie MediaPlayer in een geldige staat voor dit bevel is, dat om het even welk behalve RELEASED of FOUT is.
1. Roep `setVolume` op de instantie `MediaPlayer` aan om het audiovolume in te stellen.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   De waarde voor het volume geeft het gevraagde volume weer, uitgedrukt in verhouding tot het maximale volume, waarbij 0 stil is en 100 het maximale volume.

