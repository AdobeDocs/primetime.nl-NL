---
title: Lokaal gegenereerde CRL's gebruiken
description: Lokaal gegenereerde CRL's gebruiken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Lokaal gegenereerde CRL&#39;s gebruiken{#consume-locally-generated-crls}

Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL&#39;s) en beleidsupdate wilt gebruiken, gebruikt u API&#39;s van Adobe Access om de handtekening te verifiëren. APIs verifieert dat de lijsten niet met zijn geknoeid en dat zij door de correcte Server van de Vergunning werden ondertekend.

* Vraag `RevocationList.verifySignature` om de handtekening te controleren alvorens RevocationList aan om het even welke APIs te verstrekken.

   Zie `RevocationListFactory` in de *API-naslaggids voor Adobe Access* voor meer informatie.

* Roep `PolicyUpdateList.verifySignature`aan om de handtekening te controleren alvorens `PolicyUpdateList` aan om het even welke APIs te verstrekken.

   Zie `PolicyUpdateList` in de *API-naslaggids voor Adobe Access* voor meer informatie.

