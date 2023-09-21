---
description: U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.
title: Laattijdige-binding audio integreren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# Laattijdige-binding audio integreren {#integrate-late-binding-audio}

U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.

* Een alternatief audiobeheer maken:

  ```java
  AAManager aaManager = new AAManagerOn(); 
  ```

* Om ManagerFactory te gebruiken om afwisselende audio toe te laten, zorg ervoor de volgende coderegel in is `PlayerFragment.java` bestand:

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>true</b>,config, mediaPlayer);
  ```

  Alternatieve audio uitschakelen:

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>false</b>,config, mediaPlayer);
  ```
