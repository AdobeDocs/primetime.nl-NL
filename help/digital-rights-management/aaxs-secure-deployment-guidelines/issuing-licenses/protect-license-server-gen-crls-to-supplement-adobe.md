---
title: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
description: CRL's genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# CRL&#39;s genereren ter aanvulling van de profielen die door Adobe worden gepubliceerd{#generate-crls-to-supplement-those-published-by-adobe}

Met Adobe Access kunt u CRL&#39;s maken als aanvulling op de computer-CRL die door Adobe wordt gepubliceerd. De Toegang SDK van de Adobe controleert en handhaaft de Adobe CRLs, nochtans, kunt u extra cliëntmachines verbieden door tot CRL te leiden die extra machinereferenties terugtrekt. Om dit te doen, moet u CRL tot de Toegang SDK van de Adobe overgaan, dan, wanneer het uitgeven van een vergunning, controleert SDK zowel Adobe CRL als uw eigen CRL.

Voor meer informatie over het genereren van CRL&#39;s raadpleegt u `RevocationListFactory` in *API-naslaggids voor Adobe*.
