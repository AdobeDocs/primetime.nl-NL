---
description: U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.
seo-description: U kunt in de speler op de laatste band of alternatieve audiostreams integreren door een andere audiofunctiebeheerder te maken.
seo-title: Laattijdige-binding audio integreren
title: Laattijdige-binding audio integreren
uuid: cd2e259a-2af4-4d7b-a856-79bd087e8ca6
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Laattijdige-binding audio integreren {#integrate-late-binding-audio}

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

