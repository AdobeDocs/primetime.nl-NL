---
description: U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.
title: Laattijdige-binding audio integreren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# De late-binding audio {#integrate-late-binding-audio} integreren

U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.

* Een alternatief audiobeheer maken:

   ```java
   AAManager aaManager = new AAManagerOn(); 
   ```

* Om ManagerFactory te gebruiken om afwisselende audio toe te laten, zorg ervoor de volgende lijn van code in het `PlayerFragment.java` dossier is:

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>true</b>,config, mediaPlayer);
   ```

   Alternatieve audio uitschakelen:

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>false</b>,config, mediaPlayer);
   ```

