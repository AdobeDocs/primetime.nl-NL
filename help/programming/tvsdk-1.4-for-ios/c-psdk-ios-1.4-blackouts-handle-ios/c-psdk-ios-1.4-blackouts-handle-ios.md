---
description: TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.
seo-description: TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.
seo-title: Stroomuitval in live streams verwerken
title: Stroomuitval in live streams verwerken
uuid: 1f70a272-bc77-4d41-a999-b076cb42ac5e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Stroomuitval in live streams verwerken{#handle-blackouts-in-live-streams}

TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.

Het meest gebruikte geval bij een programmastroomuitval is wanneer uw speler-app alternatieve inhoud biedt aan gebruikers die niet in aanmerking komen om de hoofdstream te bekijken. Deze app kan de TVSDK gebruiken om het begin en het einde van de brainstormperiode te bepalen. Op deze manier kan bij het begin van de stroomperiode worden overgeschakeld van de hoofdstream naar een andere stream en vervolgens worden teruggeschakeld naar de hoofdstream wanneer de stroomperiode is verstreken.

Om de oplossing voor dit gebruiksgeval uit te voeren:

1. Stel uw app in om u te abonneren op brainstormtags in een live streaming manifest.

   TVSDK is niet direct op de hoogte van brainstormtags, maar uw app kan zich abonneren op meldingen wanneer specifieke tags worden aangetroffen tijdens het parseren van manifestbestanden.
1. Voeg een meldingslistener toe voor `PTTimedMetadataChangedNotification`.

   Deze melding wordt telkens verzonden wanneer een geabonneerde tag in het manifest wordt geparseerd en er een nieuwe tag uit `PTTimedMetadata` wordt voorbereid.

1. Een listenermethode implementeren, zoals `onMediaPlayerSubscribedTagIdentified`voor `PTTimedMetadata` objecten op de voorgrond.

1. Telkens wanneer er tijdens het afspelen een update plaatsvindt, gebruikt u de `PTMediaPlayerTimeChangeNotification` listener om `PTTimedMetadata` objecten af te handelen.

1. Voeg de `PTTimedMetadata` handler toe.

   Met deze handler kunt u schakelen naar alternatieve inhoud en terugkeren naar de hoofdinhoud, zoals aangegeven door het `PTTimedMetadata` object en de afspeeltijd.

1. Gebruik deze optie `onSubscribedTagInBackground` om de listenermethode voor `PTTimedMetadata` objecten op de achtergrond te implementeren.

   Deze methode controleert de timing op de achtergrondstroom, die u helpt bepalen wanneer u van afwisselende inhoud terug naar de belangrijkste inhoud kunt schakelen.

1. Een listenermethode implementeren voor achtergrondfouten.
1. Als het bereik van de black-out zich in de DVR op de afspeelstream bevindt, werkt u de niet-doorzoekbare bereiken bij.

   In de volgende gevallen moet het bereik voor niet-zoekbare gegevens in de DVR worden ingesteld:

   * Bij aansluiting van de hoofdstroom wanneer een stroomstoring zich in de DVR bevindt.
   * Wanneer u vanuit de alternatieve inhoud teruggaat naar de hoofdinhoud.

