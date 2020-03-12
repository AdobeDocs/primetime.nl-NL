---
description: U kunt stroomstoringen in live videostreams verwerken en tijdens een stroomstoring alternatieve inhoud bieden.
seo-description: U kunt stroomstoringen in live videostreams verwerken en tijdens een stroomstoring alternatieve inhoud bieden.
seo-title: Stroomuitval in live streams verwerken
title: Stroomuitval in live streams verwerken
uuid: df933087-c8a8-49eb-a016-6dfd971c219c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Stroomuitval in live streams verwerken{#handle-blackouts-in-live-streams}

U kunt stroomstoringen in live videostreams verwerken en tijdens een stroomstoring alternatieve inhoud bieden.

Wanneer een brainstormsessie plaatsvindt in een live stream, gebruikt de speler gebeurtenishandlers om de brainstormsessie te detecteren en biedt deze gebruikers alternatieve inhoud die niet in aanmerking komen om de hoofdstream te bekijken. De speler detecteert het begin en einde van de periode van stroomuitval, schakelt het afspelen van de hoofdstream over naar een alternatieve stream en schakelt terug naar de hoofdstream wanneer de periode van stroomuitval eindigt.

In uw client-app meldt u zich aan voor black-out-tags in TVSDK. Nadat u op de hoogte bent gesteld van nieuwe *metagegevensobjecten* met tijdslimiet, parseert u de gegevens van het metagegevensobject met tijdslimiet om te bepalen of het object een brainstormsessie of uitgang aangeeft. Voor geïdentificeerde stroomuitval roept u de relevante TVSDK-elementen op om naar alternatieve inhoud te schakelen aan het begin van de stroomuitval, en nogmaals om terug te keren naar de belangrijkste inhoud wanneer de stroomuitval voorbij is.

>[!TIP]
>
>De sleutels worden nog gedownload van manifest alvorens de inhoud wordt gespeeld.

Wanneer een gebruiker verbinding maakt met een live stream nadat de black-out-periode is verstreken en op tijd terugschuift naar de &#39;blacted-out&#39;-periode, wordt de inhoud afgespeeld.

>[!IMPORTANT]
>
>Als alle zeer belangrijke verzoeken ontbreken, wordt een fout geworpen wanneer het ontleden van manifest. Als sommige aanvragen mislukken en sommige succesvol zijn, probeert TVSDK de inhoud af te spelen. Als TVSDK een sectie van de inhoud probeert af te spelen, maar er geen geldige sleutel is om deze inhoud te decoderen, wordt een fout geretourneerd.

Stroomuitval in live streams afhandelen:

1. Stel uw app in om black-out-tags te detecteren door u te abonneren op black-out-tags in een live-streaming manifest.

   TVSDK detecteert alleen geen black-out-tags; u moet zich abonneren op brainstormtags om meldingen te ontvangen wanneer de tags tijdens het parseren van manifestbestanden worden aangetroffen.
1. Maak gebeurtenislisteners voor tags waarop de speler is geabonneerd.

   Wanneer een tag voorkomt waarop de speler heeft geabonneerd (bijvoorbeeld een black-out tag) in de manifests van de voor- (hoofdinhoud) of de achtergrond (alternatieve inhoud), verzendt TVSDK een tag `TimedMetadataEvent` en maakt een `TimedMetadataObject` voor de `TimedMetadataEvent`.
1. Implementeer handlers voor de getimede metagegevensgebeurtenissen voor zowel de voorgrond- als de achtergrondstreams.

   In deze handlers, krijg de begin en eindtijden voor de zwartoutperiode van de getimed voorwerpen van de meta-gegevensgebeurtenis.
1. De voorinstelling voorbereiden `MediaPlayer` op stroomuitval.

   Wanneer de status PREPARED `MediaPlayer` wordt ingeschakeld, berekent en bereidt u de stroombereiken voor en stelt u deze in op het `MediaPlayer` object.

1. Controleer voor elke update van de positie van de afspeelkop de lijst met `TimedMetadataObjects`.

   Hier detecteert uw speler het begin en einde van de black-out en volgt de tijd van de black-out op het moment dat deze plaatsvindt.

1. Methoden maken voor het schakelen tussen inhoud aan het begin en einde van de periode van uitschakeling.

   Wanneer de brainstormperiode begint, schakelt u de hoofdinhoud over naar de achtergrond en schakelt u de alternatieve inhoud om als de hoofdstream te worden. Ga door met het ophalen en parseren van het oorspronkelijke manifest op de achtergrond en blijf controleren op de tag &quot;black-out end&quot;, zodat de speler zich opnieuw bij de oorspronkelijke stream kan aansluiten wanneer de black-out eindigt.

