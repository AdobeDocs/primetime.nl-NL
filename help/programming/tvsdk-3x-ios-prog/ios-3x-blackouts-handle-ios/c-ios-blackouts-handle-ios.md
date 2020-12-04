---
description: TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.
seo-description: TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.
seo-title: Verwerking verwerken
title: Verwerking verwerken
uuid: 00b6f204-6ba4-4245-9028-6f7c392e9275
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Stroomuitval verwerken {#handle-blackouts}

TVSDK handelt stroomonderbrekingen in live videostreams af en biedt alternatieve inhoud tijdens een stroomstoring.

Het meest gebruikte geval bij een programmastroomuitval is wanneer uw speler-app alternatieve inhoud biedt aan gebruikers die niet in aanmerking komen om de hoofdstream te bekijken. Deze app kan de TVSDK gebruiken om het begin en het einde van de brainstormperiode te bepalen. Op deze manier kan bij het begin van de stroomperiode worden overgeschakeld van de hoofdstream naar een andere stream en vervolgens worden teruggeschakeld naar de hoofdstream wanneer de stroomperiode is verstreken.

Om de oplossing voor dit gebruiksgeval uit te voeren:

1. Stel uw app in om u te abonneren op brainstormtags in een live streaming manifest.

   TVSDK is niet direct op de hoogte van brainstormtags, maar uw app kan zich abonneren op meldingen wanneer specifieke tags worden aangetroffen tijdens het parseren van manifestbestanden.
1. Voeg een berichtluisteraar voor `PTTimedMetadataChangedNotification` toe.

   Deze melding wordt elke keer verzonden wanneer een geabonneerde tag in het manifest wordt geparseerd en er wordt een nieuwe `PTTimedMetadata` uit voorbereid.

1. Voer een luisteraarmethode, zoals `onMediaPlayerSubscribedTagIdentified`, voor `PTTimedMetadata` voorwerpen in voorgrond uit.

1. Elke keer dat er tijdens het afspelen een update plaatsvindt, gebruikt u de `PTMediaPlayerTimeChangeNotification`-listener om `PTTimedMetadata`-objecten af te handelen.

1. Voeg de `PTTimedMetadata` manager toe.

   Met deze handler kunt u schakelen naar alternatieve inhoud en terugkeren naar de hoofdinhoud, zoals aangegeven door het object `PTTimedMetadata` en de afspeeltijd.

1. Gebruik `onSubscribedTagInBackground` om de listenermethode voor `PTTimedMetadata`-objecten op de achtergrond te implementeren.

   Deze methode controleert de timing op de achtergrondstroom, die u helpt bepalen wanneer u van afwisselende inhoud terug naar de belangrijkste inhoud kunt schakelen.

1. Een listenermethode implementeren voor achtergrondfouten.
1. Als het bereik van de black-out zich in de DVR op de afspeelstream bevindt, werkt u de niet-doorzoekbare bereiken bij.

   In de volgende gevallen moet het bereik voor niet-zoekbare gegevens in de DVR worden ingesteld:

   * Bij aansluiting van de hoofdstroom wanneer een stroomstoring zich in de DVR bevindt.
   * Wanneer u vanuit de alternatieve inhoud teruggaat naar de hoofdinhoud.