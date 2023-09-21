---
description: Als de toepassing gebeurtenissen moet verwerken die worden verzonden vanuit functiebeheer, moet deze de manager registreren in het bestand PlayerFragment.java.
title: Gebeurtenissen afhandelen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
