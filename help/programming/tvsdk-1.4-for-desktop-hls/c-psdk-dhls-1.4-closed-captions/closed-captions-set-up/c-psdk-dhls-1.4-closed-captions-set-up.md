---
description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
seo-description: Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.
seo-title: Werken met gesloten bijschriften
title: Werken met gesloten bijschriften
uuid: 881266aa-3c32-4035-9547-0f363949f77b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---


# Werken met gesloten bijschriften{#work-with-closed-captions}

Bij Closed Captioning wordt het audiogedeelte van een video als tekst op het scherm weergegeven wanneer het geluid onhoorbaar is of de kijker niet goed kan worden gehoord.

Gesloten bijschriften hebben doorgaans dezelfde taal als de audio en geven ook achtergrondgeluiden weer als tekst, maar ondertitels zijn doorgaans in een andere taal en bevatten geen achtergrondgeluiden.

TVSDK ondersteunt het renderen van deze indelingen:

* 608 en 708 ondertiteling, wanneer geleverd als deel van de videovervoerstroom over HLS als gegevenspakketten in MPEG-2 videostromen.
* WebVTT-ondertitelingsbestanden, waarnaar wordt verwezen vanuit de M3U8-manifestbestanden zoals gedefinieerd in de HLS-specificaties. Ze zijn automatisch beschikbaar als Closed Caption-tracks in de Primetime-speler.

U kunt:

* Selecteer een beschikbare bijschrifttrack als huidige track en luister naar gebeurtenissen die aangeven welke aanvullende beschikbare tracks beschikbaar zijn.
* Schakel ondertiteling aan of uit (zichtbaar of niet zichtbaar) door de `MediaPlayer` interface te gebruiken.
* Selecteer opmaakopties die bepalen hoe gesloten bijschriften worden gerenderd door de onderliggende video-engine. Gebruik de `MediaPlayerItem` interface om formaten zoals de doopvont of doopvontkleur te selecteren.

