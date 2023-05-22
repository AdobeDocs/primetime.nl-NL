---
description: 302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.
title: HTTP 302-herleidingsoptimalisatie
exl-id: a238e90f-3aa1-486b-b57f-d543e4c94b2e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# HTTP 302-herleidingsoptimalisatie {#http-redirect-optimization}

302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.

Als een hoofdmanifestverzoek wordt omgeleid, en optimalisering 302 in uw speler wordt toegelaten, zullen de verdere verzoeken die voor activa van dat manifest worden gemaakt de definitieve domeinplaats gebruiken, die extra 302 reacties vermijdt. Deze functie is standaard ingeschakeld en u kunt deze instelling wijzigen.

## 302 omleidingsoptimalisatie uitschakelen of inschakelen {#section_8977448B268E41D69A8F75B60EB9DA3B}

Gebruik de `useRedirectedUrl` eigenschap om 302 omleiding in te schakelen ( `true`) of uit ( `false`).

<!--<a id="example_888749F70C8A43279D06A29BD68E7E4D"></a>-->

Bijvoorbeeld:

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration on MediaPlayerItemConfig 
MediaPlayerItemConfig config = new MediaPlayerItemConfig (); 
config.setNetworkConfiguration(networkConfiguration); 
 
//Use this config when loading the MediaPlayerItem or calling replaceCurrentResource
```
