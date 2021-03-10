---
description: U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.
title: Een aangepast beginpunt voor DVR kiezen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Een aangepast beginpunt kiezen voor DVR {#choosing-a-custom-starting-point-for-dvr}

U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.

De begintijd instellen via de klasse [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html):

1. Schakel [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()) in.
1. Stel de begintijd in [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Controleer of de aangepaste startpositie is ingeschakeld.
