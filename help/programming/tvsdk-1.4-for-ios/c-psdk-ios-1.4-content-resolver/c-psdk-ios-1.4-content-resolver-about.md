---
description: TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.
title: Opportuniteitsgeneratoren en contentoplosers
exl-id: 86722bdc-cb50-4739-8322-7cce4667b297
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Opportuniteitsgeneratoren en contentoplosers{#opportunity-generators-and-content-resolvers}

Een opportuniteitsdetector is een TVSDK-component die aangepaste tags in een stream detecteert en plaatsingsmogelijkheden identificeert. Deze mogelijkheden worden naar de inhoudoplosser verzonden, die de inhoud/toevoegingswerkstroom op de eigenschappen van de plaatsingskans en meta-gegevens aanpast.

TVSDK bevat een standaardopportuniteitsdetector:

* `PTOpportunityResolver`, die standaard en aanwijzingen begrijpt

TVSDK bevat ook een standaardinhoudsoplosser die inhoud bevat die moet worden ingevoegd op basis van de metagegevenssleutel in het speleritem:

* `PTContentResolver`

U kunt de standaardopportuniteitsdetectors en inhoudsoplossers overschrijven om de advertentieworkflow op de volgende manieren aan te passen:

* Ondersteuning voor aangepaste tagdetectie toevoegen
* Eigen tags herkennen voor invoegen van advertentie
* Een aangepaste advertentieprovider maken
* Inhoud onleesbaar maken

TVSDK biedt standaard opportuniteitsgeneratoren en inhoudsoplossers die advertenties in de tijdlijn plaatsen, en deze generatoren en oplossers zijn gebaseerd op niet-standaardlabels in het manifest. Uw toepassing zou de chronologie kunnen moeten veranderen die op kansen wordt gebaseerd die in manifest, zoals indicatoren voor een zwartoutperiode worden geïdentificeerd.

An *`opportunity`* vertegenwoordigt een interessepunt op de chronologie die gewoonlijk op een kans van de advertentie wijst. Deze kans kan ook een aangepaste bewerking aangeven die de tijdlijn kan beïnvloeden, zoals een uitvalperiode. An *`opportunity generator`* identificeert specifieke kansen (markeringen) in de chronologie en deelt TVSDK mee dat deze kansen zijn geëtiketteerd. De kansen worden geïdentificeerd in een chronologie in `PTTimedMetadata` door een niet-standaard (niet-HLS)-tag op te nemen.

Wanneer uw toepassing een melding krijgt over een opportuniteit (tag), kan uw toepassing de tijdlijn wijzigen door bijvoorbeeld een reeks advertenties in te voegen, over te schakelen op een alternatieve stream (black-outs) of door de tijdlijninhoud op een andere manier te bewerken. Door gebrek, roept TVSDK aangewezen *`content resolver`* om de vereiste tijdlijnwijzigingen of -handelingen te implementeren. Uw toepassing kan de standaardinhoudsoplosser voor TVSDK-advertenties gebruiken of een eigen inhoudoplosser registreren.

U kunt ook `PTSDKConfig.setAdTags` meer tags/aanwijzingen voor advertenties toevoegen zodat TVSDK deze kan herkennen en gebruiken `PTSDKConfig.setSubscribedTags` en informeer uw toepassing over extra tags die informatie over de advertentieworkflow kunnen bevatten.

Een van de mogelijke toepassingen van een aangepaste oplosser is voor brainstormperioden. Om deze periodes af te handelen, kan uw toepassing een black-out opportuniteitsdetector implementeren en registreren die verantwoordelijk is voor de afhandeling van black-out tags. Wanneer TVSDK deze tag aantreft, worden alle geregistreerde contentoplossers opgezocht om de eerste te vinden die de opgegeven tag afhandelt. In dit voorbeeld is dit de oplosser voor stroominhoud, die bijvoorbeeld het huidige item kan vervangen door alternatieve inhoud op de speler voor de duur die door de tag wordt opgegeven.
