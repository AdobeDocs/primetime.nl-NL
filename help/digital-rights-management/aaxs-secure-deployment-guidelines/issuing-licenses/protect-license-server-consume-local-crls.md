---
seo-title: Lokaal gegenereerde CRL's gebruiken
title: Lokaal gegenereerde CRL's gebruiken
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

