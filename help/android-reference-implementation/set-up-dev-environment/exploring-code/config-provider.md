---
description: De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.
title: ConfigProvider
exl-id: 75613bfb-3c2b-4b53-b365-adc98f7e1164
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# ConfigProvider {#configprovider}

De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.

U gebruikt de [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) klasse die de `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`, en `IQosConfig` de configuratieinterfaces zodat de eigenschapmanagers de configuraties kunnen lezen. De `ICCConfig` is de interface voor de `CCManager` configuratie. De configuratiedossiers ontvangen de configuratieparameters van het JSON configuratiedossier.

De `ConfigProvider.java` file is een voorbeeld van Adobe implementatie van de configuratieinterfaces. De instellingen worden gelezen vanuit `SharedPreferences`, waar de configuratie wordt opgeslagen. U kunt uw configuratie opslaan op om het even welke manier die voor uw organisatie werkt. De config implementatie verstrekt een omslag voor uw configuratiebron.
