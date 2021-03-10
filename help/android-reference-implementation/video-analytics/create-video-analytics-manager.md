---
description: Manager voor videoanalyse maken
title: Manager voor videoanalyse maken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Manager {#create-the-video-analytics-manager} voor videoanalyse maken

Er is een nieuwe beheerklasse ( `VAManager`) toegevoegd aan de Android Reference Implementation. `VAManager` maakt en vernietigt eenvoudig een instantie van de  `VideoHeartbeat` klasse. De verwijzingsimplementatie leidt tot een `VAManager` instantie wanneer nieuw `MediaPlayer` wordt gecreeerd, en vernietigt die instantie wanneer `MediaPlayer` wordt vernietigd. Dit wordt geïmplementeerd in `PlayerFragment.java`.

## Een nieuwe Video Analytics Manager maken

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

De configuratievariabele is een concrete implementatie van `IVAConfig` en bevat runtime `VideoHeartbeat` configuraties.

>[!NOTE]
>
>Als de Android-toepassing niet is geconfigureerd met een Adobe Analytics-account, worden geen gegevens voor het bijhouden van video gegenereerd, zelfs niet als een instantie van `VAManager` is gemaakt en ingeschakeld.

