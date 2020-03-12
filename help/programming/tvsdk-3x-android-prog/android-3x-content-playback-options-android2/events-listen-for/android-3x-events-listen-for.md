---
description: Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
seo-description: Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.
seo-title: Luisteren naar gebeurtenissen in Primetime Player
title: Luisteren naar gebeurtenissen in Primetime Player
uuid: 3aa0979c-6141-4098-9f19-d5fe23192827
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Overzicht {#listen-for-primetime-player-events-overview}

Gebeurtenissen van TVSDK geven de status van de speler aan, fouten die optreden, de voltooiing van handelingen die u hebt aangevraagd, zoals een video die wordt afgespeeld, of handelingen die impliciet optreden, zoals een advertentie-bewerking.

Omdat uw toepassing op veel van deze gebeurtenissen moet reageren, moet u gebeurtenis-behandelende routines uitvoeren en deze routines registreren met TVSDK. De routines roepen de relevante methodes TVSDK om geschikt te antwoorden.

Meer informatie over gebeurtenissen:

* Het afspelen van video in realtime vereist asynchrone (niet-blokkerende) activiteit voor veel TVSDK-bewerkingen.
* TVSDK ondersteunt een gebeurtenisgestuurde videospeler.

   Het biedt gebeurtenissen die overeenkomen met alle belangrijke stappen in het afspeelproces. U registreert die gebeurtenissen met het gebeurtenismechanisme van uw platform en creeert gebeurtenismanagers die zullen worden geroepen wanneer die gebeurtenissen voorkomen. *`Event Handlers`* worden ook callback-routines of gebeurtenislisteners genoemd. TVSDK biedt een volledig scala aan methoden die door de gebeurtenishandlers kunnen worden gebruikt.
* In de toepassing worden gewoonlijk niet-blokkerende bewerkingen gestart, zoals het aanvragen van het afspelen van een video.

   TVSDK communiceert asynchroon met uw toepassing door gebeurtenissen te verzenden, zoals wanneer de video begint met afspelen en een gebeurtenis wanneer de video is voltooid. Andere gebeurtenissen kunnen statuswijzigingen in de speler en foutcondities aangeven. Uw gebeurtenishandlers voeren de juiste handelingen uit.