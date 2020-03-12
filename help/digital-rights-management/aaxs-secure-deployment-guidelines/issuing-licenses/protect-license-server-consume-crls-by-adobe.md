---
seo-title: CRL's van Adobe gebruiken
title: CRL's van Adobe gebruiken
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# CRL&#39;s van Adobe gebruiken{#consume-crls-published-by-adobe}

De SDK downloadt periodiek door Adobe gepubliceerde CRL&#39;s. Blokkeer de toegang tot deze bestanden niet en belet de handhaving van deze CRL&#39;s niet.

De SDK heeft een configuratieoptie om fouten te negeren bij het ophalen van de Adobe CRL&#39;s. Deze optie mag alleen worden gebruikt in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s van Adobe kunnen ophalen. Het niet verkrijgen van een geldig CRL is een fout.
