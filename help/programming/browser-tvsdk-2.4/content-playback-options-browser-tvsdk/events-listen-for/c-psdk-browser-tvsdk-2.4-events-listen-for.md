---
description: Gebeurtenissen van Browser-TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die begint met afspelen, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
seo-description: Gebeurtenissen van Browser-TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die begint met afspelen, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
seo-title: Luisteren naar gebeurtenissen in Primetime Player
title: Luisteren naar gebeurtenissen in Primetime Player
uuid: 7b7c28ac-22ae-46a3-bbeb-bef1b04baeb3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Overzicht {#listen-for-primetime-player-events-overview}

Gebeurtenissen van Browser-TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die begint met afspelen, of handelingen die impliciet optreden, zoals een advertentie-bewerking.

Omdat uw toepassing op veel van deze gebeurtenissen moet antwoorden, moet u gebeurtenis-behandelende routines uitvoeren en deze routines met Browser TVSDK registreren. De routines roepen de relevante Browser methodes van TVSDK om geschikt te antwoorden.

Hieronder vindt u aanvullende informatie over gebeurtenissen:

* Het afspelen van video in realtime vereist asynchrone (niet-blokkerende) activiteit voor veel TVSDK-bewerkingen in Browser.
* Browser-TVSDK ondersteunt een gebeurtenisgestuurde videospeler.

   Het biedt gebeurtenissen die overeenkomen met alle belangrijke stappen in het afspeelproces. U registreert die gebeurtenissen met het gebeurtenismechanisme van uw platform en creeert gebeurtenismanagers die zullen worden geroepen wanneer die gebeurtenissen voorkomen. *`Event Handlers`* worden ook callback-routines of gebeurtenislisteners genoemd. Browser TVSDK verstrekt een volledige waaier van methodes die door de gebeurtenismanagers kunnen worden gebruikt.
* In de toepassing worden gewoonlijk niet-blokkerende bewerkingen gestart, zoals het aanvragen van het afspelen van een video.

   Browser TVSDK communiceert asynchroon met uw toepassing door gebeurtenissen, zoals wanneer de video begint te spelen en een gebeurtenis te verzenden wanneer de video eindigt. Andere gebeurtenissen kunnen statuswijzigingen in de speler en foutcondities aangeven. Uw gebeurtenishandlers voeren de juiste handelingen uit.

