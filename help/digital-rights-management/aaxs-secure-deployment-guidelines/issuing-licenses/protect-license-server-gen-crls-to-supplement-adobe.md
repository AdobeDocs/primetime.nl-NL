---
seo-title: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
title: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
uuid: 4e93f6d3-5a04-44e9-9e6b-e878798b68f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# CRL&#39;s genereren ter aanvulling van de profielen die worden gepubliceerd door Adobe{#generate-crls-to-supplement-those-published-by-adobe}

Met Adobe Access kunt u CRL&#39;s maken als aanvulling op de computer-CRL die door Adobe wordt gepubliceerd. Adobe Access SDK controleert en dwingt de Adobe CRL&#39;s af, maar u kunt extra clientcomputers uitschakelen door een CRL te maken dat extra computerreferenties herroept. Om dit te doen, moet u CRL tot Adobe Access SDK overgaan, toen, wanneer het uitgeven van een vergunning, SDK zowel de Adobe CRL als uw eigen CRL controleert.

Voor meer informatie over het produceren van CRLs, zie `RevocationListFactory` in *Adobe Toegang API Verwijzing*.
