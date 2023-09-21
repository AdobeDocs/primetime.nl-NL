---
title: Verpakkingsopties
description: Verpakkingsopties
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---

# Verpakkingsopties{#packaging-options}

U hebt een groot aantal opties voor het verpakken van inhoud. U kunt de opties opgeven in het dialoogvenster `DRMParameters` interface en implementeer de klassen die een interface kunnen maken. Met deze klassen kunt u parameters voor handtekening en sleutel instellen en aangeven of audio-inhoud, video-inhoud of scriptgegevens moeten worden gecodeerd. Om te zien hoe deze in de verwijzingsimplementatie worden uitgevoerd, zie de beschrijvingen van de opties van de het bevellijn van Media Packager in *Adobe Primetime DRM Reference Implementations gebruiken*. Deze opties zijn gebaseerd op de Java API en zijn dus beschikbaar voor programmatisch gebruik.

U kunt onder andere de volgende verpakkingsopties kiezen:

* Coderingsopties (audio, video, gedeeltelijke codering).
* De server-URL van de licentie die de client gebruikt als basis-URL voor alle aanvragen die naar de licentieserver worden verzonden
* Certificaat van licentieservertransport
* Certificaat van licentieserver, gebruikt voor versleuteling van de CEK
* Packager-referentie voor het ondertekenen van metagegevens
