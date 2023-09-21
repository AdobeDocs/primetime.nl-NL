---
description: TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.
title: Verspreiden verwerken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Verspreiden verwerken {#handle-blackouts}

TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.

Het meest gebruikte geval bij een programmastroomuitval is wanneer uw speler-app alternatieve inhoud biedt aan gebruikers die niet in aanmerking komen om de hoofdstream te bekijken. Deze app kan de TVSDK gebruiken om het begin en het einde van de brainstormperiode te bepalen. Op deze manier kan bij het begin van de stroomperiode worden overgeschakeld van de hoofdstream naar een andere stream en vervolgens worden teruggeschakeld naar de hoofdstream wanneer de stroomperiode is verstreken.

Om de oplossing voor dit gebruiksgeval uit te voeren:

1. Stel uw app in om u te abonneren op black-out-tags in een live streaming manifest.

   TVSDK is niet direct op de hoogte van brainstormtags, maar uw app kan zich abonneren op meldingen wanneer specifieke tags worden aangetroffen tijdens het parseren van manifestbestanden.
1. Een meldingslistener toevoegen voor `PTTimedMetadataChangedNotification`.

   Deze melding wordt elke keer verzonden wanneer een geabonneerde tag in het manifest wordt geparseerd, en een nieuwe `PTTimedMetadata` is bereid.

1. Hiermee wordt een listenermethode geïmplementeerd, zoals `onMediaPlayerSubscribedTagIdentified`, for `PTTimedMetadata` objecten op de voorgrond.

1. Elke keer dat er een update wordt uitgevoerd tijdens het afspelen, gebruikt u de opdracht `PTMediaPlayerTimeChangeNotification` listener voor afhandeling `PTTimedMetadata` objecten.

1. Voeg de `PTTimedMetadata` handler.

   Met deze handler kunt u schakelen naar alternatieve inhoud en terugkeren naar de hoofdinhoud, zoals wordt aangegeven door de `PTTimedMetadata` object en de afspeeltijd ervan.

1. Gebruiken `onSubscribedTagInBackground` om de listenermethode voor `PTTimedMetadata` objecten op de achtergrond.

   Deze methode controleert de timing op de achtergrondstroom, die u helpt bepalen wanneer u van afwisselende inhoud terug naar de belangrijkste inhoud kunt schakelen.

1. Een listenermethode implementeren voor achtergrondfouten.
1. Als het bereik van de black-out zich in de DVR op de afspeelstream bevindt, werkt u de niet-doorzoekbare bereiken bij.

   In de volgende gevallen moet het bereik voor niet-zoekbare gegevens in de DVR worden ingesteld:

   * Bij aansluiting van de hoofdstroom wanneer een stroomstoring zich in de DVR bevindt.
   * Wanneer u vanuit de alternatieve inhoud teruggaat naar de hoofdinhoud.
