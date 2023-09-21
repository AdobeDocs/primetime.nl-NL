---
keywords: setSecure;VideoEngineView
title: Schermopname inschakelen
description: Schermopname inschakelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# Schermopname inschakelen{#enable-screen-capture}

TVSDK schakelt standaard schermvastlegging uit. De speler roept `setSecure(true)` op de `com.adobe.ave.VideoEngineView` object in constructietijd. U hebt toegang tot dit object omdat u een `VideoEngineView` object en leveren aan de `VideoEngine` object.

Schermvastlegging in uw app inschakelen:

1. De constructor `com.adobe.ave.VideoEngineView` object.
1. Bellen `setSecure(false)` op uw `VideoEngineView` object.
