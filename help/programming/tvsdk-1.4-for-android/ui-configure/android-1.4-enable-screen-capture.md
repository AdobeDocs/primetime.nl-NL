---
keywords: setSecure;VideoEngineView
title: Schermopname inschakelen
description: Schermopname inschakelen
copied-description: true
exl-id: 5dd1bf4e-ab50-4b57-89e4-eacc291a9fe3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# Schermopname inschakelen{#enable-screen-capture}

TVSDK schakelt standaard schermvastlegging uit. De speler roept `setSecure(true)` op de `com.adobe.ave.VideoEngineView` object in constructietijd. U hebt toegang tot dit object omdat u een `VideoEngineView` object en leveren aan de `VideoEngine` object.

Schermvastlegging in uw app inschakelen:

1. De `com.adobe.ave.VideoEngineView` object.
1. Bellen `setSecure(false)` op uw `VideoEngineView` object.
