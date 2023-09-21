---
description: Adobe Primetime DRM is een geavanceerde Digital Rights Management (DRM) en een oplossing voor inhoudsbescherming voor hoogwaardige audiovisuele inhoud. In toepassingen die het maken van Java API's ondersteunen, kunt u de Primetime DRM SDK gebruiken om DRM-beleid op te geven, dat beleid toe te passen op de inhoud en die inhoud te coderen.
title: Nieuw in Adobe Primetime DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Nieuw in Adobe Primetime DRM{#what-is-new-in-adobe-primetime-drm}

Adobe Primetime DRM is een geavanceerde Digital Rights Management (DRM) en een oplossing voor inhoudsbescherming voor hoogwaardige audiovisuele inhoud. In toepassingen die het maken van Java API&#39;s ondersteunen, kunt u de Primetime DRM SDK gebruiken om DRM-beleid op te geven, dat beleid toe te passen op de inhoud en die inhoud te coderen.

>[!NOTE]
>
>Primetime DRM werd vroeger genoemd Toegang van de Adobe, en voorafgaand aan dat, Flash Access.

Hier volgt een doorloopprocedure op hoog niveau voor inhoudsbeveiliging:

1. Gebruik de DRM Java API&#39;s om DRM-beleidseigenschappen en -versleutelingsparameters in te stellen.
1. Creeer een beleid DRM dat de gebruiksrollen voor om het even welke inhoud beschrijft.

   U kunt een willekeurig aantal DRM-beleidsregels maken. De meeste gebruikers creëren een klein aantal beleid, en passen hen op vele dossiers toe.
1. Een mediabestand verpakken.

   *`Packaging a file`* betekent dat u het bestand versleutelt en vervolgens een DRM-beleid toepast op het bestand.
1. Voer de licentieserver uit om een licentie aan de gebruiker uit te geven.

Als deze stappen zijn voltooid, is uw gecodeerde inhoud gereed voor implementatie. Na de implementatie kan een client een licentie aanvragen bij de licentieserver en na ontvangst kan de inhoud worden afgespeeld.

De Primetime DRM SDK biedt een Java API om deze taken uit te voeren. De SDK bevat voorbeeldimplementaties van de licentieserver en opdrachtregelprogramma&#39;s, die beide gebaseerd zijn op de Java API&#39;s van de DRM SDK.

De hieronder beschreven functies zijn nieuw in deze release.

## Nieuwe functies {#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **Harde stop -** U kunt opgeven of het afspelen wordt gestopt of voortgezet aan het einde van een afspeelvenster.
* **Afstandsafhankelijke uitvoerbesturingselementen -** U kunt uitvoerbeperkingen opgeven op basis van pixelresoluties.
* **Anonymization van de Reacties van de Server van de Vergunning -** Om de privacy met de protocollen van de Server van de Vergunning te verbeteren Primetime DRM, zal het serienummer van het vervoercertificaat voor de reacties van de vergunningsserver aan ondersteunende cliënten worden gecentreerd.
