---
description: U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.
title: Een aangepast beginpunt voor DVR kiezen
exl-id: 9813bf60-a91d-4376-a5fe-02311b73e8a0
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Een aangepast beginpunt voor DVR kiezen {#choosing-a-custom-starting-point-for-dvr}

U kunt een douaneuitgangspunt kiezen voor wanneer om een stroom in te gaan DVR in plaats van het standaardgedrag om de stroom DVR bij het begin in te gaan gebruikend de klasse ConfigProvider.

De begintijd instellen via de [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) klasse:

1. Inschakelen [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. De begintijd instellen in [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Controleer of de aangepaste startpositie is ingeschakeld.
