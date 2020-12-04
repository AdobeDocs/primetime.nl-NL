---
description: U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.
seo-description: U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.
seo-title: Een aangepast beginpunt voor DVR kiezen
title: Een aangepast beginpunt voor DVR kiezen
uuid: a7e13865-2b86-4234-ac4c-9a5320b293db
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Een aangepast beginpunt kiezen voor DVR {#choosing-a-custom-starting-point-for-dvr}

U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.

De begintijd instellen via de klasse [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html):

1. Schakel [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()) in.
1. Stel de begintijd in [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Controleer of de aangepaste startpositie is ingeschakeld.
