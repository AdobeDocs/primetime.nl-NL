---
description: Manager voor videoanalyse maken
title: Manager voor videoanalyse maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Manager voor videoanalyse maken {#create-the-video-analytics-manager}

Een nieuwe beheerklasse ( `VAManager`) is toegevoegd aan de Android Reference Implementation. `VAManager` maakt en vernietigt eenvoudig een instantie van de `VideoHeartbeat` klasse. De referentie-implementatie leidt tot een `VAManager` instantie wanneer een nieuwe `MediaPlayer` wordt gemaakt en vernietigt die instantie wanneer de `MediaPlayer` wordt vernietigd. Dit wordt geïmplementeerd in `PlayerFragment.java`.

## Een nieuwe Video Analytics Manager maken

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

De configuratievariabele is een concrete implementatie van `IVAConfig` en bevat de runtime `VideoHeartbeat` configuraties.

>[!NOTE]
>
>Als de Android-toepassing niet is geconfigureerd met een Adobe Analytics-account, worden er geen gegevens voor het bijhouden van video&#39;s gegenereerd, zelfs niet als een instantie van `VAManager` wordt gemaakt en ingeschakeld.
