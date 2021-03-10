---
description: Als de toepassing gebeurtenissen moet verwerken die worden verzonden vanuit functiebeheer, moet deze de manager registreren in het bestand PlayerFragment.java.
title: Gebeurtenissen afhandelen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 4%

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
