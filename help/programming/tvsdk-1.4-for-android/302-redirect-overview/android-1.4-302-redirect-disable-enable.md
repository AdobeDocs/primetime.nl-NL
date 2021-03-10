---
description: 302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.
title: 302 omleidingsoptimalisatie uitschakelen of inschakelen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 1%

---


# HTTP 302-herleidingsoptimalisatie {#http-302-redirect-optimization}

302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.

Als een hoofdmanifestverzoek wordt omgeleid, en optimalisering 302 in uw speler wordt toegelaten, zullen de verdere verzoeken die voor activa van dat manifest worden gemaakt de definitieve domeinplaats gebruiken, die extra 302 reacties vermijdt.

Deze functie is standaard ingeschakeld en u kunt deze instelling wijzigen.

## 302 omleidingsoptimalisatie uitschakelen of inschakelen{#disable-or-enable-redirect-optimization}

Gebruik de eigenschap `useRedirectedUrl` om 302 omleiding in of uit te schakelen (true).
Bijvoorbeeld:

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration as Metadata: 
MetadataNode resourceMetadata = new MetadataNode();  
resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                         networkConfiguration); 
 
//Call MediaResource.createFromURL to set the metadata: 
MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
  
//Load the resource 
mediaPlayer.replaceCurrentItem(resource);
```

