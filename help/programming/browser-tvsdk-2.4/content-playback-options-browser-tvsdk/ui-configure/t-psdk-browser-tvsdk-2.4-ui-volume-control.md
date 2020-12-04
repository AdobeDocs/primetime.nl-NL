---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
seo-description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
seo-title: Volumeregeling opgeven
title: Volumeregeling opgeven
uuid: 5f2f69cc-3969-4ca2-8ab9-5713fdf5cdb8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '101'
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

