---
description: TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.
seo-description: TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.
seo-title: Opportuniteitsgeneratoren en contentoplosers
title: Opportuniteitsgeneratoren en contentoplosers
uuid: 35823336-5338-4cdc-8778-e73cd1d05251
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# Opportuniteitsgeneratoren en inhoudsoplossers {#opportunity-generators-and-content-resolvers}

TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.

Een *`opportunity`* staat voor een interessant punt op de tijdlijn dat meestal een plaatsingsmogelijkheid aangeeft. Deze kans kan ook een aangepaste bewerking aangeven die de tijdlijn kan beïnvloeden, zoals een uitvalperiode. Een *`opportunity generator`* identificeert specifieke kansen (markeringen) in de chronologie en deelt TVSDK mee dat deze kansen zijn geëtiketteerd. De kansen worden geïdentificeerd in een chronologie binnen door een niet-standaard (niet-HLS) markering op te nemen.

Wanneer uw toepassing op de hoogte wordt gesteld van een opportuniteit, kan deze de tijdlijn wijzigen door een reeks advertenties in te voegen, over te schakelen op een alternatieve stream (black-outs) of door de inhoud van de tijdlijn op een andere manier te bewerken. Standaard roept TVSDK de juiste *`content resolver`* aan om de vereiste tijdlijnwijzigingen of -handelingen te implementeren. Uw toepassing kan de standaardinhoudsoplosser voor TVSDK-advertenties gebruiken of een eigen inhoudoplosser registreren.

U kunt `MediaPlayerItemConfig.setAdTags` ook gebruiken om meer tags/aanwijzingen voor advertenties toe te voegen, zodat TVSDK `MediaPlayerItemConfig.subscribedTags` kan herkennen en gebruiken en uw toepassing op de hoogte kan stellen van extra tags die mogelijk informatie over de advertentieworkflow bevatten.

Een van de mogelijke toepassingen van een aangepaste oplosser is voor brainstormperioden. Om deze periodes af te handelen, kan uw toepassing een black-out opportuniteitsdetector implementeren en registreren die verantwoordelijk is voor de afhandeling van black-out tags. Wanneer TVSDK deze tag aantreft, worden alle geregistreerde contentoplossers opgezocht om de eerste te vinden die de opgegeven tag afhandelt. In dit voorbeeld is dit de oplosser voor stroominhoud, die bijvoorbeeld het huidige item kan vervangen door alternatieve inhoud op de speler voor de duur die door de tag wordt opgegeven.
