---
description: TVSDK downloadt de advertentiesegmenten en rendert deze op het scherm van het apparaat.
title: Ad-playbackfase
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Ad-playbackfase{#ad-playback-phase}

TVSDK downloadt de advertentiesegmenten en rendert deze op het scherm van het apparaat.

Op dit moment heeft TVSDK advertenties opgelost, op de tijdlijn geplaatst en geprobeerd de inhoud op het scherm weer te geven.

De volgende hoofdklassen van fouten kunnen in deze fase voorkomen:

* Fouten bij het verbinden met de hostserver
* Fouten bij het downloaden van het manifestbestand
* Fouten bij het downloaden van de mediasegmenten

Voor alle drie foutklassen heeft TVSDK gebeurtenissen doorgestuurd naar uw toepassing, waaronder:

* Gebeurtenissen van het bericht teweeggebracht wanneer een failover gebeurt.
* Gebeurtenissen van het bericht wanneer het profiel wegens het failoveralgoritme wordt veranderd.
* Gebeurtenissen van het bericht teweeggebracht wanneer alle failoveropties zijn overwogen, en geen extra actie kan automatisch worden ondernomen.

  Uw toepassing moet de juiste actie ondernemen.

Of er fouten optreden of niet, TVSDK roept onAdBreakComplete aan voor elke fout `onAdBreakStart` en `onAdComplete` voor elke `onAdStart`. Als segmenten echter niet kunnen worden gedownload, bevat de tijdlijn mogelijk tussenruimten. Wanneer de tussenruimten groot genoeg zijn, kunnen de waarden in de positie van de afspeelkop en de gerapporteerde en de voortgang discontinuïteit vertonen.
