---
description: TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.
title: Opportuniteitsgeneratoren en contentoplosers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Opportuniteitsgeneratoren en contentoplosers{#opportunity-generators-and-content-resolvers}

TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.

An *`opportunity`* vertegenwoordigt een interessepunt op de chronologie die gewoonlijk op een kans van de advertentie wijst. Deze kans kan ook een aangepaste bewerking aangeven die de tijdlijn kan beïnvloeden, zoals een uitvalperiode. An *`opportunity generator`* identificeert specifieke kansen (markeringen) in de chronologie en deelt TVSDK mee dat deze kansen zijn geëtiketteerd. De kansen worden geïdentificeerd in een chronologie in `TimedMetadata`. De `SpliceOutOpportunityGenerator` biedt mogelijkheden op basis van de `TimedMetadata` objecten die zijn gemaakt voor elke advertentietag die in het manifest is gedetecteerd, en de `AdSignalingModeOpportunityGenerator` creëert de eerste kans die gebaseerd is op de `MediaPlayerItem` type en de bijbehorende advertentiemodus.

Wanneer uw toepassing een melding krijgt over een opportuniteit (tag), kan uw toepassing de tijdlijn wijzigen door bijvoorbeeld een reeks advertenties in te voegen, over te schakelen op een alternatieve stream (black-outs) of door de tijdlijninhoud op een andere manier te bewerken. Door gebrek, roept TVSDK aangewezen *`content resolver`* om de vereiste tijdlijnwijzigingen of -handelingen te implementeren. Uw toepassing kan de standaardinhoudsoplosser voor TVSDK-advertenties gebruiken of een eigen inhoudoplosser registreren.

U kunt ook `PSDKConfig.adTags` om meer tags/aanwijzingen voor de standaardmarkeertekens toe te voegen `SpliceOutOpportunityGenerator` klasse en gebruik `PSDKConfig.setSubscribedTags` zodat TVSDK uw toepassing op de hoogte kan stellen van aanvullende tags die informatie over de publicatieworkflow kunnen bevatten.

Een van de mogelijke toepassingen van een aangepaste oplosser is voor brainstormperioden. Om deze periodes af te handelen, kan uw toepassing een black-out opportuniteitsdetector implementeren en registreren die verantwoordelijk is voor de afhandeling van black-out tags. Wanneer TVSDK deze tag aantreft, worden alle geregistreerde contentoplossers opgezocht om de eerste te vinden die de opgegeven tag afhandelt. In dit voorbeeld is dit de oplosser voor stroominhoud, die bijvoorbeeld het huidige item kan vervangen door alternatieve inhoud op de speler voor de duur die door de tag wordt opgegeven.
