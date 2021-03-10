---
description: Met Adobe Primetime DRM kunt u CRL's maken die een aanvulling vormen op de computer-CRL die door Adobe wordt gepubliceerd.
title: CRL’s genereren ter aanvulling van de door Adobe gepubliceerde CRL’s
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# CRL&#39;s genereren ter aanvulling van de door Adobe{#generating-crls-to-supplement-those-published-by-adobe} gepubliceerde CRL&#39;s

Met Adobe Primetime DRM kunt u CRL&#39;s maken die een aanvulling vormen op de computer-CRL die door Adobe wordt gepubliceerd.

De Primetime DRM SDK controleert en handhaaft de Adobe CRLs. U kunt echter aanvullende clientcomputers weigeren door een CRL te maken dat aanvullende computergegevens herroept door het CRL door te geven aan de Primetime DRM SDK. Wanneer u een licentie geeft, controleert de SDK de Adobe CRL en uw CRL.

Om CRLs te produceren, zie [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).
