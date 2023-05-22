---
title: CRL's van Adobe gebruiken
description: CRL's van Adobe gebruiken
copied-description: true
exl-id: b7f68a29-f834-4613-b64d-e610f660e6fc
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# CRL&#39;s van Adobe gebruiken{#consume-crls-published-by-adobe}

De SDK downloadt periodiek CRL&#39;s die door Adobe worden gepubliceerd. Blokkeer de toegang tot deze bestanden niet en belet de handhaving van deze CRL&#39;s niet.

SDK heeft een configuratieoptie om fouten te negeren wanneer het terugwinnen van Adobe CRLs. Deze optie mag alleen worden gebruikt in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s van Adobe kunnen ophalen. Het niet verkrijgen van een geldig CRL is een fout.
