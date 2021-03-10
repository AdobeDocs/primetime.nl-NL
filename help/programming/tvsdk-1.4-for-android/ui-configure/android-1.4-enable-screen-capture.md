---
keywords: setSecure;VideoEngineView
title: Schermopname inschakelen
description: Schermopname inschakelen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# Schermopname inschakelen{#enable-screen-capture}

TVSDK schakelt standaard schermvastlegging uit. De speler roept `setSecure(true)` op het `com.adobe.ave.VideoEngineView` voorwerp in bouwtijd. U hebt toegang tot dit object, aangezien u een `VideoEngineView`-object moet maken en dit aan het `VideoEngine`-object moet leveren.

Schermvastlegging in uw app inschakelen:

1. Hiermee wordt het object `com.adobe.ave.VideoEngineView` samengesteld.
1. Roep `setSecure(false)` op uw `VideoEngineView` voorwerp.
