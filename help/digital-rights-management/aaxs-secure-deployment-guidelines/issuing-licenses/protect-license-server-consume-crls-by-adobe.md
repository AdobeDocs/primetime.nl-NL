---
title: CRL's die door Adobe worden gepubliceerd, gebruiken
description: CRL's die door Adobe worden gepubliceerd, gebruiken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# CRL&#39;s die door Adobe worden gepubliceerd, gebruiken{#consume-crls-published-by-adobe}

De SDK downloadt periodiek CRL&#39;s die door de Adobe worden gepubliceerd. Blokkeer de toegang tot deze bestanden niet en belet de handhaving van deze CRL&#39;s niet.

SDK heeft een configuratieoptie om fouten te negeren wanneer het terugwinnen van de Adobe CRLs. Deze optie mag alleen worden gebruikt in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s van de Adobe kunnen ophalen. Het niet verkrijgen van een geldig CRL is een fout.
