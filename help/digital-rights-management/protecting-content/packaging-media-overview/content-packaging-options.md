---
title: Verpakkingsopties
description: Verpakkingsopties
copied-description: true
exl-id: 64c5c22d-0041-4fb9-80d0-72e11cb775f3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---

# Verpakkingsopties{#packaging-options}

U hebt een groot aantal opties voor het verpakken van inhoud. U kunt de opties opgeven in het dialoogvenster `DRMParameters` interface en implementeer de klassen die een interface kunnen maken. Met deze klassen kunt u parameters voor handtekening en sleutel instellen en aangeven of audio-inhoud, video-inhoud of scriptgegevens moeten worden gecodeerd. Om te zien hoe deze in de verwijzingsimplementatie worden uitgevoerd, zie de beschrijvingen van de opties van de het bevellijn van Media Packager in *Adobe Primetime DRM Reference Implementations gebruiken*. Deze opties zijn gebaseerd op de Java API en zijn dus beschikbaar voor programmatisch gebruik.

De volgende verpakkingsopties zijn beschikbaar:

* Coderingsopties (audio, video, gedeeltelijke codering).
* De server-URL van de licentie die de client gebruikt als basis-URL voor alle aanvragen die naar de licentieserver worden verzonden
* Certificaat van licentieservertransport
* Certificaat van licentieserver, gebruikt voor versleuteling van de CEK
* Packager-referentie voor het ondertekenen van metagegevens
