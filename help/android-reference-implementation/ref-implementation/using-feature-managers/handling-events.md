---
description: Als de toepassing gebeurtenissen moet verwerken die worden verzonden vanuit functiebeheer, moet deze de manager registreren in het bestand PlayerFragment.java.
seo-description: Als de toepassing gebeurtenissen moet verwerken die worden verzonden vanuit functiebeheer, moet deze de manager registreren in het bestand PlayerFragment.java.
seo-title: Gebeurtenissen afhandelen
title: Gebeurtenissen afhandelen
uuid: 13639f02-0dcc-4a0a-8524-515da5478006
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 2%

---


# Gebeurtenissen {#handling-events} verwerken

Als de toepassing gebeurtenissen moet verwerken die worden verzonden vanuit functiebeheer, moet deze de manager registreren in het bestand PlayerFragment.java.

Bijvoorbeeld:

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
