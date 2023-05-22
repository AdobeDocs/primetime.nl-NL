---
description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
title: Werken met gesloten bijschriften
exl-id: e93725e3-6c6d-42b8-83d0-0feb4f9be50b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Overzicht {#work-with-closed-captions-overview}

Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.

Gesloten bijschriften hebben doorgaans dezelfde taal als de audio en geven ook achtergrondgeluiden weer als tekst, maar ondertitels zijn doorgaans in een andere taal en bevatten geen achtergrondgeluiden.

TVSDK ondersteunt het renderen van deze indelingen:

* 608 en 708 ondertiteling, wanneer geleverd als deel van de videovervoerstroom over HLS als gegevenspakketten in MPEG-2 videostromen.
* WebVTT-ondertitelingsbestanden, waarnaar wordt verwezen vanuit de M3U8-manifestbestanden zoals gedefinieerd in de HLS-specificaties.

   Deze bestanden zijn automatisch beschikbaar als Closed Caption-tracks in de Primetime-speler.

U kunt het volgende doen:

* Selecteer een beschikbare bijschrifttrack als huidige track en luister naar gebeurtenissen die aangeven welke aanvullende beschikbare tracks beschikbaar zijn.
* Schakel ondertiteling sluiten in (zichtbaar) of uit (niet zichtbaar) door de `MediaPlayer` interface.
* Selecteer opmaakopties die bepalen hoe gesloten bijschriften worden gerenderd door de onderliggende video-engine.

   Gebruik de `MediaPlayerItem` interface voor het selecteren van indelingen zoals het lettertype of de lettertypekleur.
