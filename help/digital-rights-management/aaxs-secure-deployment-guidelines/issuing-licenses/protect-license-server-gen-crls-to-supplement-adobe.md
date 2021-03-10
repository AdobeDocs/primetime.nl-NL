---
title: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
description: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# CRL&#39;s genereren ter aanvulling van de profielen die worden gepubliceerd door Adobe{#generate-crls-to-supplement-those-published-by-adobe}

Met Adobe Access kunt u CRL&#39;s maken als aanvulling op de computer-CRL die door Adobe wordt gepubliceerd. Adobe Access SDK controleert en dwingt de Adobe CRL&#39;s af, maar u kunt extra clientcomputers uitschakelen door een CRL te maken dat extra computerreferenties herroept. Om dit te doen, moet u CRL tot Adobe Access SDK overgaan, toen, wanneer het uitgeven van een vergunning, SDK zowel de Adobe CRL als uw eigen CRL controleert.

Voor meer informatie over het produceren van CRLs, zie `RevocationListFactory` in *Adobe Toegang API Verwijzing*.
