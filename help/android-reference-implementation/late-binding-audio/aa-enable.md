---
description: U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.
title: Laattijdige-binding audio integreren
exl-id: 43be9042-d547-4646-a920-cdd2a5dbb1fb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
