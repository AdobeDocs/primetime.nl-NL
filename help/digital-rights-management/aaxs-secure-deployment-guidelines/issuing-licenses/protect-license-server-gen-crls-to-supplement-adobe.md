---
seo-title: CRL's genereren ter aanvulling van de door Adobe gepubliceerde profielen
title: CRL's genereren ter aanvulling van de door Adobe gepubliceerde profielen
uuid: 4e93f6d3-5a04-44e9-9e6b-e878798b68f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# CRL&#39;s genereren ter aanvulling van de door Adobe gepubliceerde profielen{#generate-crls-to-supplement-those-published-by-adobe}

Met Adobe Access kunt u CRL&#39;s maken als aanvulling op de computer-CRL die door Adobe wordt gepubliceerd. De SDK van Adobe Access controleert en dwingt Adobe CRL&#39;s af, maar u kunt extra clientcomputers uitschakelen door een CRL te maken dat extra computergegevens herroept. Hiervoor moet u de CRL doorgeven aan de Adobe Access SDK. Bij het uitgeven van een licentie controleert de SDK zowel Adobe CRL als uw eigen CRL.

Zie `RevocationListFactory` in de *Adobe Access API-naslaggids* voor meer informatie over het genereren van CRL&#39;s.
