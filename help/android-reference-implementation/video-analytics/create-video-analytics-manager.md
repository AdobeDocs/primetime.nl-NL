---
description: Manager voor videoanalyse maken
seo-description: Manager voor videoanalyse maken
seo-title: Manager voor videoanalyse maken
title: Manager voor videoanalyse maken
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Manager voor videoanalyse maken {#create-the-video-analytics-manager}

Er is een nieuwe beheerklasse ( `VAManager`) toegevoegd aan de Android Reference Implementation. `VAManager` maakt en vernietigt eenvoudig een instantie van de `VideoHeartbeat` klasse. De verwijzingsimplementatie leidt tot een `VAManager` geval wanneer een nieuw `MediaPlayer` wordt gecreeerd, en vernietigt die instantie wanneer het `MediaPlayer` wordt vernietigd. Dit wordt geïmplementeerd in `PlayerFragment.java`.

## Een nieuwe Video Analytics Manager maken

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

De configuratievariabele is een concrete implementatie van `IVAConfig` en bevat de runtime `VideoHeartbeat` configuraties.

>[!NOTE]
>
>Als de Android-toepassing niet is geconfigureerd met een Adobe Analytics-account, worden er geen gegevens voor het bijhouden van video&#39;s gegenereerd, zelfs niet als een instantie van `VAManager` wordt gemaakt en ingeschakeld.

