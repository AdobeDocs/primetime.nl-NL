---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumeregeling opgeven
exl-id: aa8ffdf3-515b-4899-8a00-8fb5b8c595a9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Volumeregeling opgeven{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht tot de instantie MediaPlayer in een geldige staat voor dit bevel is, dat om het even welk behalve RELEASED of FOUT is.
1. Bellen `setVolume` op de `MediaPlayer` -instantie om het audiovolume in te stellen.

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   De waarde voor het volume geeft het gevraagde volume weer, uitgedrukt in verhouding tot het maximale volume, waarbij 0 stil is en 100 het maximale volume.
