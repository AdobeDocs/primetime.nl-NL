---
description: Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.
title: Opportuniteitsgeneratoren en contentoplosers
exl-id: a47acd22-8b1b-4c66-a7eb-a4d99afb5f17
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Opportuniteitsgeneratoren en contentoplosers{#opportunity-generators-and-content-resolvers}

Browser TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest worden geïdentificeerd.

An *`opportunity`* vertegenwoordigt een interessepunt op de chronologie die gewoonlijk op een kans van de advertentie wijst. Deze mogelijkheid kan ook een aangepaste bewerking aangeven die de tijdlijn kan beïnvloeden. An *`opportunity generator`* identificeert specifieke kansen (markeringen) in de chronologie en deelt TVSDK mee dat deze kansen zijn geëtiketteerd.

De kansen worden geïdentificeerd in een chronologie in `TimedMetata`. De `ManifestCuesOpportunityGenerator` biedt mogelijkheden op basis van de `TimedMetadata` objecten die worden gemaakt voor elke splice-out en -tag (in `MediaPlayerItemConfig.adTags`) die in het manifest is aangetroffen. De `AdSignalingModeOpportunityGenerator` creëert de eerste kans die gebaseerd is op de `MediaPlayerItem` type en de bijbehorende advertentiemodus.

>[!TIP]
>
>Als de `AdvertisingMetadata.livePreroll` of de `AdvertisingMetadata.preroll` eigenschap is ingesteld, `AdSignalingModeOpportunityGenerator` genereert een pre-roll mogelijkheid voor live streams.

Wanneer uw toepassing op de hoogte wordt gesteld van een opportuniteit (tag), kan uw toepassing de tijdlijn wijzigen door bijvoorbeeld een reeks advertenties in te voegen. Door gebrek, roept Browser TVSDK aangewezen *`content resolver`* om de vereiste tijdlijnwijzigingen of -handelingen te implementeren. Uw toepassing kan de standaardinhoudsoplosser voor TVSDK-advertenties in de browser gebruiken of een eigen inhoudoplosser registreren.

U kunt ook `MediaPlayerItemConfig.adTags` om meer tags/aanwijzingen voor de standaardmarkeertekens voor advertenties toe te voegen `ManifestCuesOpportunityGenerator` klasse en gebruik `MediaPlayerItemConfig.subscribedTags` zodat TVSDK uw toepassing op de hoogte kan stellen van aanvullende tags die informatie over de publicatieworkflow kunnen bevatten.

>[!TIP]
>
>De standaardwaarden van `MediaPlayerItemConfig.adTags` en `MediaPlayerItemConfig.subscribeTags` is `[MediaPlayerItemConfig.DEFAULT_AD_TAG]`.
