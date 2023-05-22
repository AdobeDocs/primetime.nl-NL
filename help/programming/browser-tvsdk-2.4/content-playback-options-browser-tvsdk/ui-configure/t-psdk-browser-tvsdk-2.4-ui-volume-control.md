---
description: U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.
title: Volumeregeling opgeven
exl-id: 5c446081-5491-46b6-9259-293131af80cb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# Volumeregeling opgeven{#provide-volume-control}

U kunt een gebruikersinterfacecontrole voor geluidsvolume instellen.

1. Wacht op de `MediaPlayer` -instantie in een geldige status voor deze opdracht.

   Elke status behalve RELEASED of ERROR is geldig.
1. Stel het kenmerk Volume in op het tabblad `MediaPlayer` -instantie om het audiovolume in te stellen.

   ```js
   player.volume = ...
   ```

   De waarde voor het volume staat voor het gevraagde volume, uitgedrukt als een percentage van het maximumvolume, waarbij 0 stil is en het maximumvolume is.
