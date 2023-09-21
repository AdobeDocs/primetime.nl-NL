---
description: Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
title: Luisteren naar gebeurtenissen in Primetime Player
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Overzicht {#listen-for-primetime-player-events-overview}

Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.

Omdat uw toepassing op veel van deze gebeurtenissen moet antwoorden, moet u gebeurtenis-behandelende routines uitvoeren en deze routines met TVSDK registreren. De routines roepen de relevante methodes TVSDK om geschikt te antwoorden.

Hieronder vindt u aanvullende informatie over gebeurtenissen:

* Het afspelen van video in realtime vereist asynchrone (niet-blokkerende) activiteit voor veel TVSDK-bewerkingen.
* TVSDK ondersteunt een gebeurtenisgestuurde videospeler.

  Het biedt gebeurtenissen die overeenkomen met alle belangrijke stappen in het afspeelproces. U registreert die gebeurtenissen met het gebeurtenismechanisme van uw platform en creeert gebeurtenismanagers die zullen worden geroepen wanneer die gebeurtenissen voorkomen. *`Event Handlers`* worden ook callback-routines of gebeurtenislisteners genoemd. TVSDK biedt een volledig scala aan methoden die door de gebeurtenishandlers kunnen worden gebruikt.
* In de toepassing worden gewoonlijk niet-blokkerende bewerkingen gestart, zoals het aanvragen van het afspelen van een video.

  TVSDK communiceert asynchroon met uw toepassing door gebeurtenissen te verzenden, zoals wanneer de video begint met afspelen en een gebeurtenis wanneer de video is voltooid. Andere gebeurtenissen kunnen statuswijzigingen in de speler en foutcondities aangeven. Uw gebeurtenishandlers voeren de juiste handelingen uit.
