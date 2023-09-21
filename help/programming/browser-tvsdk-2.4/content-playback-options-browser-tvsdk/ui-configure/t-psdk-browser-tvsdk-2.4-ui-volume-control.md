---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumecontrole bieden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Volumecontrole bieden{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht op de `MediaPlayer` -instantie in een geldige status voor deze opdracht.

   Elke status behalve RELEASED of ERROR is geldig.
1. Stel het kenmerk Volume in op het tabblad `MediaPlayer` -instantie om het audiovolume in te stellen.

   ```js
   player.volume = ...
   ```

   De waarde voor het volume staat voor het gevraagde volume, uitgedrukt als een percentage van het maximumvolume, waarbij 0 stil is en het maximumvolume is.
