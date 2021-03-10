---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumeregeling opgeven
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---


# Verstrek volumeregeling{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht tot de `MediaPlayer` instantie in een geldige staat voor dit bevel is.

   Elke status behalve RELEASED of ERROR is geldig.
1. Stel het volumekenmerk in de instantie `MediaPlayer` in om het audiovolume in te stellen.

   ```js
   player.volume = ...
   ```

   De waarde voor het volume staat voor het gevraagde volume, uitgedrukt als een percentage van het maximumvolume, waarbij 0 stil is en het maximumvolume is.

