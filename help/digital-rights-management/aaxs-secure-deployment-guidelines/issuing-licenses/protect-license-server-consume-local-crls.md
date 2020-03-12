---
seo-title: Lokaal gegenereerde CRL's gebruiken
title: Lokaal gegenereerde CRL's gebruiken
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Lokaal gegenereerde CRL&#39;s gebruiken{#consume-locally-generated-crls}

Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL&#39;s) en beleidsupdate wilt gebruiken, gebruikt u Adobe Access-API&#39;s om de handtekening te verifiëren. APIs verifieert dat de lijsten niet met zijn geknoeid en dat zij door de correcte Server van de Vergunning werden ondertekend.

* Vraag `RevocationList.verifySignature` om de handtekening te controleren alvorens RevocationList aan om het even welke APIs te verstrekken.

   Zie voor meer informatie `RevocationListFactory` in de *Adobe Access API-naslaggids*.

* Vraag `PolicyUpdateList.verifySignature`om de handtekening te controleren voordat u de handtekening aan API&#39; `PolicyUpdateList` s opgeeft.

   Zie voor meer informatie `PolicyUpdateList` in de *Adobe Access API-naslaggids*.

