---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
seo-description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
seo-title: Volumeregeling opgeven
title: Volumeregeling opgeven
uuid: 63e96424-54d0-4c16-bd94-2366722f752a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '97'
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

