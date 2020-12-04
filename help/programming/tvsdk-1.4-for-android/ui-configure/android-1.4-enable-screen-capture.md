---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: Schermopname inschakelen
title: Schermopname inschakelen
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# Schermopname inschakelen{#enable-screen-capture}

TVSDK schakelt standaard schermvastlegging uit. De speler roept `setSecure(true)` op het `com.adobe.ave.VideoEngineView` voorwerp in bouwtijd. U hebt toegang tot dit object, aangezien u een `VideoEngineView`-object moet maken en dit aan het `VideoEngine`-object moet leveren.

Schermvastlegging in uw app inschakelen:

1. Hiermee wordt het object `com.adobe.ave.VideoEngineView` samengesteld.
1. Roep `setSecure(false)` op uw `VideoEngineView` voorwerp.
