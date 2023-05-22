---
description: Manager voor videoanalyse maken
title: Manager voor videoanalyse maken
exl-id: 8d2bbb39-10e2-43e8-8ed3-bc376b3f3cc8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Manager voor videoanalyse maken {#create-the-video-analytics-manager}

Een nieuwe beheerklasse ( `VAManager`) is toegevoegd aan de Android Reference Implementation. `VAManager` maakt en vernietigt eenvoudig een instantie van de `VideoHeartbeat` klasse. Met de voorbeeldimplementatie wordt een `VAManager` instantie wanneer een nieuwe `MediaPlayer` wordt gemaakt en vernietigt die instantie wanneer de `MediaPlayer` wordt vernietigd. Dit wordt geïmplementeerd in `PlayerFragment.java`.

## Een nieuwe Video Analytics Manager maken

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

De configuratievariabele is een concrete implementatie van `IVAConfig` en bevat de runtime `VideoHeartbeat` configuraties.

>[!NOTE]
>
>Als de Android-toepassing niet is geconfigureerd met een Adobe Analytics-account, worden er geen gegevens voor het bijhouden van video&#39;s gegenereerd, zelfs niet als een instantie van `VAManager` wordt gemaakt en ingeschakeld.
