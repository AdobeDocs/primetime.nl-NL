---
description: Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.
seo-description: Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.
seo-title: Opportuniteitsgeneratoren en contentoplosers
title: Opportuniteitsgeneratoren en contentoplosers
uuid: e462ad89-1609-4efa-aa67-cfd04f045927
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Opportuniteitsgeneratoren en inhoudsoplossers{#opportunity-generators-and-content-resolvers}

Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.

Een *`opportunity`* staat voor een interessant punt op de tijdlijn dat meestal een plaatsingsmogelijkheid aangeeft. Deze mogelijkheid kan ook een aangepaste bewerking aangeven die de tijdlijn kan beïnvloeden. Een *`opportunity generator`* identificeert specifieke kansen (markeringen) in de chronologie en deelt TVSDK mee dat deze kansen zijn geëtiketteerd.

De kansen worden geïdentificeerd in een chronologie in `TimedMetata`. De `ManifestCuesOpportunityGenerator` creëert mogelijkheden op basis van de `TimedMetadata`-objecten die worden gemaakt voor elke splice-out ad tag (in `MediaPlayerItemConfig.adTags`) die in het manifest is gedetecteerd. `AdSignalingModeOpportunityGenerator` leidt tot de aanvankelijke kans die op `MediaPlayerItem` type en zijn bijbehorende het signaleren wijze gebaseerd is.

>[!TIP]
>
>Als `AdvertisingMetadata.livePreroll` of `AdvertisingMetadata.preroll` bezit wordt geplaatst, `AdSignalingModeOpportunityGenerator` produceert een pre-rolkans voor levende stromen.

Wanneer uw toepassing op de hoogte wordt gesteld van een opportuniteit (tag), kan uw toepassing de tijdlijn wijzigen door bijvoorbeeld een reeks advertenties in te voegen. Standaard roept Browser-TVSDK de juiste *`content resolver`* aan om de vereiste tijdlijnwijzigingen of -handelingen te implementeren. Uw toepassing kan de standaardinhoudsoplosser voor TVSDK-advertenties in de browser gebruiken of een eigen inhoudoplosser registreren.

U kunt `MediaPlayerItemConfig.adTags` ook gebruiken om meer tags/aanwijzingen voor advertenties toe te voegen voor de standaardklasse `ManifestCuesOpportunityGenerator` en `MediaPlayerItemConfig.subscribedTags` te gebruiken, zodat TVSDK uw toepassing op de hoogte kan stellen van extra tags die mogelijk informatie over de advertentieworkflow bevatten.

>[!TIP]
>
>De standaardwaarden van `MediaPlayerItemConfig.adTags` en `MediaPlayerItemConfig.subscribeTags` zijn `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.

