---
title: Verpakkingsopties
description: Verpakkingsopties
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Verpakkingsopties{#packaging-options}

U hebt een groot aantal opties voor het verpakken van inhoud. U kunt de opties in de `DRMParameters` interface specificeren en de klassen uitvoeren die kunnen interface. Met deze klassen kunt u parameters voor handtekening en sleutel instellen en aangeven of audio-inhoud, video-inhoud of scriptgegevens moeten worden gecodeerd. Om te zien hoe deze in de verwijzingsimplementatie worden uitgevoerd, zie de beschrijvingen van de de bevellijnopties van Media Packager in *Gebruikend de Implementaties van de Verwijzing van Adobe Primetime DRM* worden besproken. Deze opties zijn gebaseerd op de Java API en zijn dus beschikbaar voor programmatisch gebruik.

De volgende verpakkingsopties zijn beschikbaar:

* Coderingsopties (audio, video, gedeeltelijke codering).
* De server-URL van de licentie die de client gebruikt als basis-URL voor alle aanvragen die naar de licentieserver worden verzonden
* Certificaat van licentieservertransport
* Certificaat van licentieserver, gebruikt voor versleuteling van de CEK
* Packager-referentie voor het ondertekenen van metagegevens

