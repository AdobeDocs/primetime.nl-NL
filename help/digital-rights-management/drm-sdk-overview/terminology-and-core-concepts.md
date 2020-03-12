---
seo-title: Terminologie en kernbegrippen
title: Terminologie en kernbegrippen
uuid: dc269873-7b63-4c18-bada-5338f4da0edd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Terminologie en kernbegrippen{#terminology-and-core-concepts}

In dit document worden de volgende termen en concepten gebruikt:

**Consumenten**

De *consument* is de eindgebruiker die inhoud downloadt of stroomt.

**Inhoud**

*Inhoud* bestaat uit digitale audio- of videobestanden.

**Inhoudscoderingssleutel**

De CEK ( *Content Encryption Key* ) is een cryptografische sleutel die wordt gebruikt om de inhoud te versleutelen.

**Eigenaren van inhoud**

*Eigenaars* van inhoud zijn de zakelijke entiteiten die eigenaar zijn van het copyright van de inhoud. Dit kunnen grote filmstudio&#39;s zijn, of kleinere, onafhankelijke producenten van films of andere audiovisuele inhoud.

**Inhoud verpakken**

*Inhoudspakketten* zijn organisaties die inhoud verpakken voor gebruik met Adobe Primetime DRM. Eigenaren of distributeurs van inhoud kunnen ervoor kiezen hun eigen inhoud in een pakket te plaatsen, of ze kunnen de services van een derde partij inschrijven om hun inhoud te verpakken en deze elektronisch via internet te distribueren.

**Digitaal certificaat**

*Digitale certificaten* (ook wel *certificaten* genoemd) binden een entiteit, zoals een individu, organisatie of systeem, aan een specifiek openbaar en privé sleutelpaar. Digitale certificaten kunnen worden beschouwd als elektronische referenties waarmee de identiteit van een individu, systeem of organisatie wordt geverifieerd.

**Digitale handtekening**

Een *digitale handtekening* bindt de identiteit van de uitgever aan de inhoud die zij hebben gepubliceerd en verstrekt een mechanisme om het knoeien te ontdekken. Digitale handtekeningalgoritmen gebruiken cryptografische hashfuncties en asymmetrische (of openbare/persoonlijke sleutelparen) versleutelingsalgoritmen. Sommige digitale handtekeningen maken ook gebruik van digitale certificaten en PKI (Public Key Infrastructure) om openbare sleutels te binden aan de identiteit van eigenaars of distributeurs van inhoud.

**Distributeur**

*Distributeurs* (ook wel *contentdistributeurs* of* detailhandelaren* genoemd) zijn zakelijke entiteiten die distributierechten van eigenaars van inhoud veiligstellen om inhoud aan consumenten te publiceren en te verspreiden. In sommige gevallen is dezelfde entiteit zowel de eigenaar van de inhoud als de distributeur van de inhoud.

**DRM-metagegevens**

Informatie die de client (dus Adobe® Flash® Player, Adobe® AIR® runtime en Primetime client) verzendt om de gevraagde inhoud te identificeren.

**Licentie**

Een *license *is een gegevensstructuur die een gecodeerde sleutel bevat die wordt gebruikt om inhoud te decrypteren verbonden aan een beleid. De licentie wordt gegenereerd door Primetime DRM wanneer de consument om inhoud vraagt en is gebonden aan de computer van de consument. Met een beleid als referentie definieert de licentie de rechten die beschikbaar zijn voor de consument die inhoud downloadt. De consument moet een licentie krijgen om de inhoud te kunnen bekijken.

**Vergunning verkrijgen**

*Vergunningsverwerving* is het proces waarbij een licentie wordt verkregen waarmee de consument beveiligde inhoud kan decoderen en bekijken volgens een set gebruiksregels. Licentieaanschaf doet zich voor wanneer een client informatie met de gevraagde inhoud (de *DRM-metagegevens*) en het machinecertificaat (de computer van de consument identificeren) naar de licentieserver verzendt (zie hieronder).

**Licentieserver**

De* Licentieserver *kan worden geïntegreerd in de facturerings- en verificatiesystemen van de distributeur of serviceprovider en kan bedrijfslogica bevatten om te controleren of de consument die om beveiligde inhoud verzoekt, gemachtigd is om de inhoud te bekijken. Als de gebruiker gemachtigd is om tot de inhoud toegang te hebben, geeft de Server van de Vergunning een vergunning uit die de runtime cliënt toestaat om inhoud te decrypteren en te spelen die op het beleid en de rechten wordt gebaseerd verbonden aan de rekening van de consument.

U moet een licentieserver maken en implementeren met de Primetime DRM SDK.

**Beleid**

Een *beleid* is een container voor de gebruiksregels die bepalen hoe de consument beschermde inhoud kan gebruiken. Het beleid wordt onafhankelijk van de inhoud gedefinieerd die wordt beveiligd. Een beleid dwingt geen rechten af tot het aan de inhoud door de vergunning wordt gebonden. Een beleid maakt een lijst van de reeks gebruiksregels, betekenend de toestemmingen of de &quot;rechten&quot;die de consumenten aan de inhoud moeten hebben zij verwerven. Eigenaars van inhoud kunnen bijvoorbeeld een beleid maken dat ervoor zorgt dat beveiligde inhoud alleen voor een bepaalde periode toegankelijk is voor consumenten. Dit beleid wordt vervolgens toegepast op alle inhoud waarvoor de eigenaar van de inhoud deze beperking wil afdwingen.

Het beleid wordt gecreeerd gebruikend Primetime DRM SDK.

**Beveiligde inhoud**

*Beveiligde inhoud* (ook wel *verpakte inhoud* genoemd) verwijst naar video-inhoud die is gecodeerd met Primetime DRM SDK of andere ondersteunde gereedschappen.

**Detailhandelaars**

Zie de ingang voor *verdelers* vroeger in deze sectie.
