---
seo-title: Verpakkingsopties
title: Verpakkingsopties
uuid: 04244428-cb42-438a-8f16-91532c70ea60
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verpakkingsopties{#packaging-options}

U hebt een groot aantal opties voor het verpakken van inhoud. U kunt de opties in de `DRMParameters` interface specificeren en de klassen uitvoeren die kunnen interface. Met deze klassen kunt u parameters voor handtekening en sleutel instellen en aangeven of audio-inhoud, video-inhoud of scriptgegevens moeten worden gecodeerd. Zie de beschrijvingen van de opties voor de opdrachtregel van Media Packager die in de Adobe Primetime DRM-naslaggids worden besproken, voor informatie over hoe deze in de voorbeeldimplementaties ** worden geïmplementeerd. Deze opties zijn gebaseerd op de Java API en zijn dus beschikbaar voor programmatisch gebruik.

De volgende verpakkingsopties zijn beschikbaar:

* Coderingsopties (audio, video, gedeeltelijke codering).
* De server-URL van de licentie die de client gebruikt als basis-URL voor alle aanvragen die naar de licentieserver worden verzonden
* Certificaat van licentieservertransport
* Certificaat van licentieserver, gebruikt voor versleuteling van de CEK
* Packager-referentie voor het ondertekenen van metagegevens

