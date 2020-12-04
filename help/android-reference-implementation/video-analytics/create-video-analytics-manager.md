---
description: Manager voor videoanalyse maken
seo-description: Manager voor videoanalyse maken
seo-title: Manager voor videoanalyse maken
title: Manager voor videoanalyse maken
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '118'
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

