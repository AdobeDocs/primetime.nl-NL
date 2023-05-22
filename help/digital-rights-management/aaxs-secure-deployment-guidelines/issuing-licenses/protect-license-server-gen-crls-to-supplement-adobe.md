---
title: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
description: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
copied-description: true
exl-id: 05dc2159-fa7f-4772-9f25-c89370b4981e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# CRL&#39;s genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd{#generate-crls-to-supplement-those-published-by-adobe}

Met Adobe Access kunt u CRL&#39;s maken als aanvulling op de computer-CRL die door Adobe wordt gepubliceerd. Adobe Access SDK controleert en dwingt de Adobe CRL&#39;s af, maar u kunt extra clientcomputers uitschakelen door een CRL te maken dat extra computerreferenties herroept. Om dit te doen, moet u CRL tot Adobe Access SDK overgaan, toen, wanneer het uitgeven van een vergunning, SDK zowel de Adobe CRL als uw eigen CRL controleert.

Voor meer informatie over het genereren van CRL&#39;s raadpleegt u `RevocationListFactory` in *Referentie voor Adobe Access API*.
