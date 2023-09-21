---
description: U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.
title: Een aangepast beginpunt voor DVR kiezen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Een aangepast beginpunt voor DVR kiezen {#choosing-a-custom-starting-point-for-dvr}

U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.

Als u de begintijd wilt instellen via de [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) klasse:

1. Inschakelen [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. De begintijd instellen in [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Controleer of de aangepaste startpositie is ingeschakeld.
