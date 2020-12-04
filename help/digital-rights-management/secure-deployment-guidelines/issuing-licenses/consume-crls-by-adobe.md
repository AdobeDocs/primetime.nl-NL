---
description: De SDK downloadt periodiek CRL's die door Adobe worden gepubliceerd. U moet ervoor zorgen dat de toegang tot deze dossiers niet wordt geblokkeerd of de handhaving van deze CRLs niet wordt verhinderd.
seo-description: De SDK downloadt periodiek CRL's die door Adobe worden gepubliceerd. U moet ervoor zorgen dat de toegang tot deze dossiers niet wordt geblokkeerd of de handhaving van deze CRLs niet wordt verhinderd.
seo-title: CRL's gebruiken die door Adobe zijn gepubliceerd
title: CRL's gebruiken die door Adobe zijn gepubliceerd
uuid: 7a9088bd-dde6-4445-958c-3e7272215b3c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# CRL&#39;s gebruiken die zijn gepubliceerd door Adobe{#consuming-crls-published-by-adobe}

De SDK downloadt periodiek CRL&#39;s die door Adobe worden gepubliceerd. U moet ervoor zorgen dat de toegang tot deze dossiers niet wordt geblokkeerd of de handhaving van deze CRLs niet wordt verhinderd.

SDK heeft een configuratieoptie om fouten te negeren bij het ophalen van Adobe CRL&#39;s en u kunt deze optie alleen toepassen in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s ophalen van Adobe. Als de licentieserver geen geldige CRL kan verkrijgen, is er een fout opgetreden.
