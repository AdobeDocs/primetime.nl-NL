---
title: Lokaal gegenereerde CRL's gebruiken
description: Lokaal gegenereerde CRL's gebruiken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Lokaal gegenereerde CRL&#39;s gebruiken{#consume-locally-generated-crls}

Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL&#39;s) en beleidsupdate wilt gebruiken, gebruikt u API&#39;s voor toegang tot Adobe om de handtekening te verifiëren. APIs verifieert dat de lijsten niet met zijn geknoeid en dat zij door de correcte Server van de Vergunning werden ondertekend.

* Bellen `RevocationList.verifySignature` om de handtekening te controleren voordat de RevocationList wordt doorgegeven aan API&#39;s.

  Zie voor meer informatie `RevocationListFactory` in de *API-naslaggids voor Adobe*.

* Bellen `PolicyUpdateList.verifySignature`om de handtekening te controleren voordat u de `PolicyUpdateList` naar API&#39;s.

  Zie voor meer informatie `PolicyUpdateList` in de *API-naslaggids voor Adobe*.
