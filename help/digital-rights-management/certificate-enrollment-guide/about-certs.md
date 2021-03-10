---
title: Certificaten
description: Certificaten
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Informatie over certificaten {#about-certificates}

De Adobe Primetime DRM SDK is beschikbaar in de volgende configuraties:

* Primetime DRM Production SDK
* Primetime DRM Evaluation SDK
* Primetime DRM-proefversie van SDK

Als u de Primetime DRM SDK wilt gebruiken om een licentieserver te maken, moet u digitale certificaten verkrijgen van Adobe. Digitale certificaten (die eenvoudig ook als certificaten worden bedoeld) binden een entiteit, zoals een individu, een organisatie, of een systeem, aan een specifiek openbaar en privé zeer belangrijk paar. Digitale certificaten kunnen worden beschouwd als elektronische referenties waarmee de identiteit van een individu, systeem of organisatie wordt geverifieerd.

Voor maximale flexibiliteit en verbeterde beveiliging in uw implementatieopties vereist de Primetime DRM SDK vier certificaten:

* Certificaat van licentieserver

   De SDK gebruikt dit certificaat om inhoudslicenties te ondertekenen die aan clients zijn uitgegeven.
* Packager-certificaat

   De SDK gebruikt dit certificaat om DRM-metagegevens te genereren bij het verpakken (versleutelen) van inhoud.
* Vervoerscertificaat

   De SDK gebruikt dit certificaat om de communicatie tussen de clients en de licentieserver te beveiligen.
* Domain CA-certificaat

   De klanten die een domeinserver willen uitvoeren hebben het certificaat van CA van het Domein nodig. In tegenstelling tot de andere certificaten, wordt het certificaat van CA van het Domein niet uitgegeven door Adobe.

>[!NOTE]
>
>Voor de Evaluatie SDK en de Proefversie SDK, worden de Server van de Vergunning, Packager, en de certificaten van het Vervoer gecombineerd in één enkel certificaat.

