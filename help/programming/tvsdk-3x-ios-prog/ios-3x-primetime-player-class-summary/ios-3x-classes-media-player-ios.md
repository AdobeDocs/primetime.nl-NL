---
description: U kunt de objectief-C API van de Speler Primetime gebruiken om het gedrag van de speler aan te passen.
seo-description: U kunt de objectief-C API van de Speler Primetime gebruiken om het gedrag van de speler aan te passen.
seo-title: Mediaspelers, klassen
title: Mediaspelers, klassen
uuid: 705c71b6-4e5e-46b5-a59d-13df977b04f2
translation-type: tm+mt
source-git-commit: b13f2d3f083a6ca333a4edba1c8d7261f7d448ad
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Mediaspelklassen {#media-player-classes}

U kunt de objectief-C API van de Speler Primetime gebruiken om het gedrag van de speler aan te passen.

Deze klassen beschrijven uw mediaspeler en de bijbehorende bronnen.

| Klasse | Beschrijving |
|---|---|
| PTABRControlParameters | Hiermee worden alle adaptieve parameters voor bitsnelheid ingekapseld. Ondersteunde parameters zijn:<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | Standaardimplementatie van PTMediaPlayerClientFactoryin de TVSDK. Het biedt de instanties availablePTOportunityResolver, PTContentResolver en PTAdPolicySelector. |
| PTMediaPlayer | Definieert de basiscomponent voor het Primetime Player-framework. Toepassingen maken een instantie van deze klasse om een media af te spelen. Deze component verzendt meldingen om de toepassing op elk gewenst moment te laten weten wat de status van de speler is. |
| PTMediaPlayerClientFactory | Protocol dat de methodes beschrijft die een de cliëntfabriek van de douanemedia speler zou moeten uitvoeren om de beschikbare instanties te verstrekken PTOportunityResolver, PTContentResolver en PTAdPolicySelector. |
| PTMediaPlayerItem | Vertegenwoordigt een specifieke audio-videomedia. |
| PTMediaPlayerView | Beheert de weergavecomponent van het Primetime Player-framework. |
| PTMediaProfile | Vertegenwoordigt het profiel van één enkele stroom in de variant playlist. |
| PTMediaSelectionOption | Vertegenwoordigt een audiovisuele mediabron die geschikt is voor verschillende taalvoorkeuren, toegankelijkheidsvereisten of aangepaste toepassingsconfiguraties. Geldige optietypen:<ul><li>Ondertitels (PTMediaSelectionOptionTypeSubtitle)</li><li>Alternatieve audio (PTMediaSelectionOptionTypeAudio)</li><li>Ondertiteling (PTMediaSelectionOptionTypeCC)</li><li>Undefined (PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolver, klasse,PTOpportResolver-protocol | Klasse die wordt gebruikt voor de verwerking van aanwijzingen in manifest die als plaatsen voor Adobe Primetime en besluitvormingsproces zullen worden gebruikt. |
| PTOplementityResolverDelegate | Protocol dat de methodes beschrijft die de oplosser van de douanemogelijkheid ( PTOportunityResolver ) zou moeten gebruiken om aan de afgevaardigde de status van het oplossen van de kans mee te delen. |
| PTSDK | Beschrijft de versie van TVSDK en zijn mogelijkheden. |
| PTSDKConfig | Hiermee worden algemene instellingen voor TVSDK beschikbaar gemaakt en kan een toepassing zich abonneren op aangepaste HLS-tags. |
| PTTextStyleRule | Definieert constanten die kenmerksleutels voor tekststijlen vertegenwoordigen die het regelwoordenboek vormen. |
