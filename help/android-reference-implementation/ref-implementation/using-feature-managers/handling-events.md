---
description: Als de toepassing gebeurtenissen moet verwerken die worden verzonden vanuit functiebeheer, moet deze de manager registreren in het bestand PlayerFragment.java.
title: Gebeurtenissen afhandelen
exl-id: 4c9a76bb-071e-4408-819c-a7611fe615cd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# Gebeurtenissen afhandelen {#handling-events}

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
