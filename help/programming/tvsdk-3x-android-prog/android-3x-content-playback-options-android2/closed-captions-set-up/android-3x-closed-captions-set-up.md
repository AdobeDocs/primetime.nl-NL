---
description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
seo-description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
seo-title: Werken met gesloten bijschriften
title: Werken met gesloten bijschriften
uuid: d7860de4-2881-4817-a4cc-5e7ab557a1db
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '240'
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
* Schakel ondertiteling sluiten in (zichtbaar) of uit (niet zichtbaar) door de `MediaPlayer` interface te gebruiken.
* Selecteer opmaakopties die bepalen hoe gesloten bijschriften worden gerenderd door de onderliggende video-engine.

   Gebruik de `MediaPlayerItem` interface om formaten zoals de doopvont of doopvontkleur te selecteren.