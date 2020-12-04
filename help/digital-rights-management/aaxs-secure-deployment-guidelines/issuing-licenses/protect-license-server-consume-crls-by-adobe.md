---
seo-title: CRL's van Adobe gebruiken
title: CRL's van Adobe gebruiken
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# CRL&#39;s van Adobe gebruiken{#consume-crls-published-by-adobe}

De SDK downloadt periodiek CRL&#39;s die door Adobe worden gepubliceerd. Blokkeer de toegang tot deze bestanden niet en belet de handhaving van deze CRL&#39;s niet.

SDK heeft een configuratieoptie om fouten te negeren wanneer het terugwinnen van Adobe CRLs. Deze optie mag alleen worden gebruikt in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s van Adobe kunnen ophalen. Het niet verkrijgen van een geldig CRL is een fout.
