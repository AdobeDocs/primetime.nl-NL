---
title: Lokaal gegenereerde CRL's gebruiken
description: Lokaal gegenereerde CRL's gebruiken
copied-description: true
exl-id: d96418d0-8fd3-4f6d-8480-191fe540080a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Lokaal gegenereerde CRL&#39;s gebruiken{#consume-locally-generated-crls}

Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL&#39;s) en beleidsupdate wilt gebruiken, gebruikt u API&#39;s van Adobe Access om de handtekening te verifiëren. APIs verifieert dat de lijsten niet met zijn geknoeid en dat zij door de correcte Server van de Vergunning werden ondertekend.

* Bellen `RevocationList.verifySignature` om de handtekening te controleren voordat de RevocationList wordt doorgegeven aan API&#39;s.

   Zie voor meer informatie `RevocationListFactory` in de *Referentie voor Adobe Access API*.

* Bellen `PolicyUpdateList.verifySignature`om de handtekening te controleren voordat u de `PolicyUpdateList` naar API&#39;s.

   Zie voor meer informatie `PolicyUpdateList` in de *Referentie voor Adobe Access API*.
