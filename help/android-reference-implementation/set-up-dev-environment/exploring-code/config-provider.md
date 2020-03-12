---
description: De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.
seo-description: De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.
seo-title: ConfigProvider
title: ConfigProvider
uuid: 2467a617-6413-4b5d-9710-894cdc751b26
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# ConfigProvider {#configprovider}

De klasse ConfigProvider krijgt de configuratie voor de media speler. U moet de configuratieinterface uitvoeren zodat kunnen de eigenschapmanagers de configuratieinformatie lezen.

U gebruikt de [klasse ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) om de `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`, en `IQosConfig` configuratieinterfaces uit te voeren zodat de eigenschapmanagers de configuraties kunnen lezen. Bijvoorbeeld, `ICCConfig` is de interface voor de `CCManager` configuratie. De configuratiedossiers ontvangen de configuratieparameters van het JSON configuratiedossier.

Het `ConfigProvider.java` bestand is een voorbeeld van de implementatie van de configuratie-interfaces door Adobe. Het leest de montages van `SharedPreferences`, waar de configuratie wordt opgeslagen. U kunt uw configuratie opslaan op om het even welke manier die voor uw organisatie werkt. De config implementatie verstrekt een omslag voor uw configuratiebron.