---
description: Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.
seo-description: Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.
seo-title: Opportuniteitsgeneratoren en contentoplosers
title: Opportuniteitsgeneratoren en contentoplosers
uuid: e462ad89-1609-4efa-aa67-cfd04f045927
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Opportuniteitsgeneratoren en contentoplosers{#opportunity-generators-and-content-resolvers}

Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.

Een object *`opportunity`* vertegenwoordigt een interessant punt op de tijdlijn dat doorgaans een plaatsingsmogelijkheid voor een advertentie aangeeft. Deze mogelijkheid kan ook een aangepaste bewerking aangeven die de tijdlijn kan beïnvloeden. Een *`opportunity generator`* identificeert specifieke kansen (markeringen) in de chronologie en deelt TVSDK mee dat deze kansen zijn geëtiketteerd.

De kansen worden geïdentificeerd in een chronologie in `TimedMetata`. De `ManifestCuesOpportunityGenerator` methode biedt mogelijkheden op basis van de `TimedMetadata` objecten die worden gemaakt voor elke splice-out en -tag (in `MediaPlayerItemConfig.adTags`) die in het manifest zijn gedetecteerd. Het `AdSignalingModeOpportunityGenerator` leidt tot de aanvankelijke kans die op het `MediaPlayerItem` type en zijn bijbehorende ad het signaleren wijze gebaseerd is.

>[!TIP]
>
>Als de eigenschap `AdvertisingMetadata.livePreroll` of de `AdvertisingMetadata.preroll` eigenschap is ingesteld, `AdSignalingModeOpportunityGenerator` wordt een pre-roll-mogelijkheid voor live streams gegenereerd.

Wanneer uw toepassing op de hoogte wordt gesteld van een opportuniteit (tag), kan uw toepassing de tijdlijn wijzigen door bijvoorbeeld een reeks advertenties in te voegen. Standaard roept Browser-TVSDK de juiste instantie aan *`content resolver`* om de vereiste tijdlijnwijzigingen of -handelingen te implementeren. Uw toepassing kan de standaardinhoudsoplosser voor TVSDK-advertenties in de browser gebruiken of een eigen inhoudoplosser registreren.

U kunt ook meer tags/aanwijzingen voor advertenties toevoegen `MediaPlayerItemConfig.adTags` voor de standaardklasse en gebruiken, `ManifestCuesOpportunityGenerator` `MediaPlayerItemConfig.subscribedTags` zodat TVSDK uw toepassing op de hoogte kan stellen van extra tags die mogelijk informatie over de advertentieworkflow bevatten.

>[!TIP]
>
>De standaardwaarden van `MediaPlayerItemConfig.adTags` en `MediaPlayerItemConfig.subscribeTags` is `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.

