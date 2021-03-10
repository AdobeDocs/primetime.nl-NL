---
description: De SDK downloadt periodiek CRL's die door Adobe worden gepubliceerd. U moet ervoor zorgen dat de toegang tot deze dossiers niet wordt geblokkeerd of de handhaving van deze CRLs niet wordt verhinderd.
title: CRL's gebruiken die door Adobe zijn gepubliceerd
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# CRL&#39;s gebruiken die zijn gepubliceerd door Adobe{#consuming-crls-published-by-adobe}

De SDK downloadt periodiek CRL&#39;s die door Adobe worden gepubliceerd. U moet ervoor zorgen dat de toegang tot deze dossiers niet wordt geblokkeerd of de handhaving van deze CRLs niet wordt verhinderd.

SDK heeft een configuratieoptie om fouten te negeren bij het ophalen van Adobe CRL&#39;s en u kunt deze optie alleen toepassen in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s ophalen van Adobe. Als de licentieserver geen geldige CRL kan verkrijgen, is er een fout opgetreden.
