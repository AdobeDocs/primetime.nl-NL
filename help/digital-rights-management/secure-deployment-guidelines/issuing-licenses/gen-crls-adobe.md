---
description: Met Adobe Primetime DRM kunt u CRL's maken die een aanvulling vormen op de computer-CRL die door Adobe wordt gepubliceerd.
seo-description: Met Adobe Primetime DRM kunt u CRL's maken die een aanvulling vormen op de computer-CRL die door Adobe wordt gepubliceerd.
seo-title: CRL’s genereren ter aanvulling van de door Adobe gepubliceerde CRL’s
title: CRL’s genereren ter aanvulling van de door Adobe gepubliceerde CRL’s
uuid: 0cc4254d-20a0-4e05-9c5b-0b84a5c833cb
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---


# CRL&#39;s genereren ter aanvulling van de door Adobe{#generating-crls-to-supplement-those-published-by-adobe} gepubliceerde CRL&#39;s

Met Adobe Primetime DRM kunt u CRL&#39;s maken die een aanvulling vormen op de computer-CRL die door Adobe wordt gepubliceerd.

De Primetime DRM SDK controleert en handhaaft de Adobe CRLs. U kunt echter aanvullende clientcomputers weigeren door een CRL te maken dat aanvullende computergegevens herroept door het CRL door te geven aan de Primetime DRM SDK. Wanneer u een licentie geeft, controleert de SDK de Adobe CRL en uw CRL.

Om CRLs te produceren, zie [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).
