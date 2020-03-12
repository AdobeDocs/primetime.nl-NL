---
description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma's, browser, netwerkverbinding en weergavecontext.
seo-description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma's, browser, netwerkverbinding en weergavecontext.
seo-title: StageVideo-mogelijkheden en -beperkingen
title: StageVideo-mogelijkheden en -beperkingen
uuid: 7556f30b-4b9f-4258-beb6-2a4ce8f05d1a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Overzicht {#stagevideo-capabilities-and-restrictions-overview}

Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma&#39;s, browser, netwerkverbinding en weergavecontext.

Met de `StageVideo` klasse kunt u gebruikmaken van hardwareversnelling om video op het hoogst mogelijke prestatieniveau voor een apparaat te presenteren. De beschikbaarheid en prestaties van `StageVideo` worden beïnvloed door de volgende factoren:

* **Hardwareversnelling** - wanneer hardwareversnelling beschikbaar is, wordt de video op de hardware van het apparaat `StageVideo` verwerkt. Wanneer hardwareversnelling niet beschikbaar is, zijn de `StageVideo` reacties afhankelijk van de versie van Flash die u uitvoert:

   * *Flash 15 en hoger* `StageVideo` - Wanneer hardwareversnelling niet beschikbaar is, wordt de software weer geactiveerd en hoeft u niets te doen.

      >[!TIP]
      >
      >Als hardwareversnelling niet beschikbaar is, kunnen de prestaties aanzienlijk afnemen.

   * *Flash 14 en eerder* - Als hardwareversnelling niet beschikbaar is, `StageVideo` wordt deze niet meer beschikbaar. In een kleine set configuraties waarbij hardwareversnelling niet wordt ondersteund door de browser of GPU of wordt uitgeschakeld in Flash Player, mislukt de videoweergave met de TVSDK HLS-stapel. In de *pijpleiding HDS* , kunt u van `StageVideo` aan een alternatief, zoals het Video voorwerp, schakelen dat video in cpu verwerkt.

* **Presentatiecontext** `StageVideo` - Tijdens weergave op volledig scherm is deze altijd beschikbaar en zijn de prestaties op het maximale niveau dat beschikbaar is op het apparaat. Wanneer de videopresentatie niet op volledig scherm wordt weergegeven, valt deze onder de context van de browser, waar de instellingen en mogelijkheden van de browser worden gebruikt.

* **wmode** - In de browsercontext is de `wmode` instelling essentieel voor de prestaties. Adobe raadt u aan deze instelling zo `wmode` `direct` in te stellen dat optimale prestaties in de browsercontext gegarandeerd zijn.

   >[!NOTE]
   >
   >De combinatie van factoren die `wmode`, `StageVideo`en Flits omvatten resulteert in verschillende mogelijkheden en beperkingen, afhankelijk van hoe snel uw hardware loopt en welke versie van Flits u gebruikt.

   * *Flash 15 en hoger* - `StageVideo` is beschikbaar met alle beschikbare `wmode` instellingen. Als u echter een andere instelling instelt `wmode` dan `direct`, zijn de prestaties lager.

   * *Flash 14 en eerder* - Als u een andere instelling instelt `wmode` dan `direct`, `StageVideo` is deze niet in alle browsers beschikbaar.

