---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: Schermopname inschakelen
title: Schermopname inschakelen
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Schermopname inschakelen{#enable-screen-capture}

TVSDK schakelt standaard schermvastlegging uit. De speler roept `setSecure(true)` het `com.adobe.ave.VideoEngineView` object tijdens de constructie aan. U hebt toegang tot dit object, aangezien u een `VideoEngineView` object moet maken en dit aan het `VideoEngine` object moet leveren.

Schermvastlegging in uw app inschakelen:

1. Construeer het `com.adobe.ave.VideoEngineView` object.
1. Roep `setSecure(false)` het `VideoEngineView` object aan.
