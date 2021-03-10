---
description: U kunt functies in- of uitschakelen zonder de code te doorlopen met behulp van de beheerfactory.
title: Functies in- of uitschakelen met ManagerFactory
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# De eigenschappen van het uitzetten of van het gebruiken van ManagerFactory{#turning-features-on-or-off-using-managerfactory}

U kunt functies in- of uitschakelen zonder de code te doorlopen met behulp van de beheerfactory.

Het argument enablement in het onderstaande voorbeeld bepaalt of de functie wordt gebruikt of niet. Als deze onwaar is, wordt de functiemanager gecreeerd maar verstrekt enkel de standaardfunctionaliteit aan de speler, alsof de eigenschapmanager niet werd gecreeerd. Als dit waar is, wordt het functiebeheer gemaakt, wordt de functie ingeschakeld en accepteert de mediaspeler invoer uit het configuratiebestand.

Bijvoorbeeld in het `com.adobe.primetime.reference.ui.player.PlayerFragment.java`-bestand:

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**API-documentatie**:  [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)