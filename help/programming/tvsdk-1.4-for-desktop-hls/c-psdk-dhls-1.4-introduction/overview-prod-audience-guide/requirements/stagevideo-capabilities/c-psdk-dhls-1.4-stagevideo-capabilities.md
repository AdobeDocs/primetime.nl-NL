---
description: Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma's, browser, netwerkverbinding en weergavecontext.
title: StageVideo-mogelijkheden en -beperkingen
exl-id: 228ea2d0-5950-43f5-8cfd-640d1c482b05
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Overzicht {#stagevideo-capabilities-and-restrictions-overview}

Op apparaten die GPU-versnelling (hardware) ondersteunen, kunt u een flash.media.StageVideo-object gebruiken om video te verwerken op het apparaat. De beschikbaarheid van StageVideo is afhankelijk van de versies en mogelijkheden van verschillende onderdelen van uw systeem, zoals Flash Player, videohardware, OS, stuurprogramma&#39;s, browser, netwerkverbinding en weergavecontext.

De `StageVideo` Met deze klasse kunt u gebruikmaken van hardwareversnelling om video op het hoogst mogelijke prestatieniveau voor een apparaat te presenteren. De beschikbaarheid en prestaties van `StageVideo` is beïnvloed door de volgende factoren:

* **Hardwareversnelling** - Wanneer hardwareversnelling beschikbaar is, `StageVideo` verwerkt video op de hardware van het apparaat. Wanneer hardwareversnelling niet beschikbaar is, wordt de `StageVideo` antwoordt is afhankelijk van de versie van de Flash die u uitvoert:

   * *Flash 15 en hoger* - Als hardwareversnelling niet beschikbaar is, `StageVideo` terugvalt op software, en je hoeft niets te doen.

      >[!TIP]
      >
      >Als hardwareversnelling niet beschikbaar is, kunnen de prestaties aanzienlijk afnemen.

   * *Flash 14 en eerder* - Als hardwareversnelling niet beschikbaar is, `StageVideo` niet meer beschikbaar is. In een kleine set configuraties waarbij hardwareversnelling niet wordt ondersteund door de browser of GPU of wordt uitgeschakeld in de Flash Player, mislukt de videoweergave met de TVSDK HLS-stapel. In de *HDS* pijpleiding, kunt u van schakelen `StageVideo` naar een alternatief, zoals het Video-object, dat video in de CPU verwerkt.

* **Presentatiecontext** - Tijdens weergave op volledig scherm, `StageVideo` is altijd beschikbaar en de prestaties zijn op het maximale niveau dat beschikbaar is op het apparaat. Wanneer de videopresentatie niet op volledig scherm wordt weergegeven, valt deze onder de context van de browser, waar de instellingen en mogelijkheden van de browser worden gebruikt.

* **wmode** - In de browsercontext `wmode` het plaatsen is kritiek aan prestaties. Adobe raadt u aan `wmode` instellen op `direct` om optimale prestaties in de browsercontext te garanderen.

   >[!NOTE]
   >
   >De combinatie van factoren die `wmode`, `StageVideo`en Flash hebben verschillende mogelijkheden en beperkingen, afhankelijk van de snelheid waarmee uw hardware wordt uitgevoerd en de versie van de Flash die u gebruikt.

   * *Flash 15 en hoger* - `StageVideo` is beschikbaar met alle beschikbare `wmode` instellingen. Als u echter `wmode` naar een andere instelling dan `direct`, zullen de prestaties lager zijn.

   * *Flash 14 en eerder* - Als u `wmode` naar een andere instelling dan `direct`, `StageVideo` is niet in alle browsers beschikbaar.
