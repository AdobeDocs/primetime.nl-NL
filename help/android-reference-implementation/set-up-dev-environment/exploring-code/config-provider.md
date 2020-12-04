---
description: De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.
seo-description: De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.
seo-title: ConfigProvider
title: ConfigProvider
uuid: 2467a617-6413-4b5d-9710-894cdc751b26
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# ConfigProvider {#configprovider}

De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.

U gebruikt de [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) klasse om `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`, en `IQosConfig` configuratieinterfaces uit te voeren zodat de eigenschapmanagers de configuraties kunnen lezen. De `ICCConfig` is bijvoorbeeld de interface voor de configuratie `CCManager`. De configuratiedossiers ontvangen de configuratieparameters van het JSON configuratiedossier.

Het `ConfigProvider.java` dossier is een voorbeeld van implementatie van de configuratieinterfaces. Het leest de montages van `SharedPreferences`, waar de configuratie wordt opgeslagen. U kunt uw configuratie opslaan op om het even welke manier die voor uw organisatie werkt. De config implementatie verstrekt een omslag voor uw configuratiebron.