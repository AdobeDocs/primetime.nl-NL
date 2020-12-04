---
description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma's, browser, netwerkverbinding en weergavecontext.
seo-description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma's, browser, netwerkverbinding en weergavecontext.
seo-title: StageVideo-mogelijkheden en -beperkingen
title: StageVideo-mogelijkheden en -beperkingen
uuid: 7556f30b-4b9f-4258-beb6-2a4ce8f05d1a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Overzicht {#stagevideo-capabilities-and-restrictions-overview}

Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma&#39;s, browser, netwerkverbinding en weergavecontext.

Met de klasse `StageVideo` kunt u gebruikmaken van hardwareversnelling om video op het hoogst mogelijke prestatieniveau voor een apparaat te presenteren. De beschikbaarheid en prestaties van `StageVideo` worden beïnvloed door de volgende factoren:

* **Hardwareversnelling** : wanneer hardwareversnelling beschikbaar is, wordt de video  `StageVideo` verwerkt op de hardware van het apparaat. Wanneer hardwareversnelling niet beschikbaar is, is het antwoord van `StageVideo` afhankelijk van de versie van Flash die u uitvoert:

   * *Flash 15 en hoger*  - Wanneer hardwareversnelling niet beschikbaar is,  `StageVideo` wordt de software opnieuw geactiveerd en hoeft u niets te doen.

      >[!TIP]
      >
      >Als hardwareversnelling niet beschikbaar is, kunnen de prestaties aanzienlijk afnemen.

   * *Flash 14 en eerder*  - Als hardwareversnelling niet beschikbaar is,  `StageVideo` wordt deze niet meer beschikbaar. In een kleine set configuraties waarbij hardwareversnelling niet wordt ondersteund door de browser of GPU of wordt uitgeschakeld in de Flash Player, mislukt de videoweergave met de TVSDK HLS-stapel. In de *HDS* pijpleiding, kunt u van `StageVideo` aan een alternatief, zoals het Video voorwerp, schakelen dat video in cpu verwerkt.

* **Presentatiecontext**  - Tijdens weergave op volledig scherm  `StageVideo` is deze altijd beschikbaar en zijn de prestaties op het maximale niveau dat beschikbaar is op het apparaat. Wanneer de videopresentatie niet op volledig scherm wordt weergegeven, valt deze onder de context van de browser, waar de instellingen en mogelijkheden van de browser worden gebruikt.

* **wmode**  - In de browsercontext is de  `wmode` instelling van essentieel belang voor de prestaties. Adobe raadt u aan `wmode` in te stellen op `direct` om de best mogelijke prestaties in de browsercontext te garanderen.

   >[!NOTE]
   >
   >De combinatie van factoren die `wmode`, `StageVideo`, en Flash omvatten resulteert in verschillende mogelijkheden en beperkingen, afhankelijk van hoe snel uw hardware loopt en welke versie van Flash u gebruikt.

   * *Flash 15 en hoger*  -  `StageVideo` is beschikbaar met alle beschikbare  `wmode` instellingen. Als u `wmode` echter instelt op een andere instelling dan `direct`, zullen de prestaties lager zijn.

   * *Flash 14 en eerder*  - Als u een andere instelling instelt  `wmode` dan  `direct`,  `StageVideo` is deze niet in alle browsers beschikbaar.

