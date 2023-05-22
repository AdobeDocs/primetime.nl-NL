---
description: De eigenschapmanagers dienen als omslagen rond de bibliotheek van TVSDK.
title: Referentie-implementatiestructuur
exl-id: cf102ccc-2e31-4197-a321-e485f77ba754
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Referentie-implementatiestructuur {#reference-implementation-structure}

De eigenschapmanagers dienen als omslagen rond de bibliotheek van TVSDK.

In Java zijn klassen gestructureerd in een hiërarchie. Bijvoorbeeld alle UI-gerelateerde code onder `com.adobe.primetime.reference.ui` en alle functies zijn ondergebracht `com.adobe.primetime.reference.manager`.

De implementatie van de Primetime-referentie bevat de volgende pakketten:

| Pakket | Beschrijving |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | Deze klasse breidt android.app.Application uit. |
| [com.adobe.primetime.reference.advertence](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | Bevat code voor aangepaste advertenties. |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | Bevat de interfacecode die voor het vormen van de eigenschapmanagers wordt vereist. |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | Bevat hulpklassen voor DRM. |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | De adapters en itemadapters voor interface, platform, en verwijzingsinformatie. Bevat ook de FeedAdapterFactory-, ContentRenditionInfo- en XMLParserHelper-code. |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | Verstrekt klassen voor het registreren plaatselijk en ver. |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | Dit is waar u de eigenschapmanagers evenals ManagerFactory kunt vinden. Voor facultatieve eigenschappen die u kunt toelaten of onbruikbaar maken, zijn er twee eigenschapmanagers: <ul><li>Één eigenschapmanager die de naam van de eigenschap, bijvoorbeeld, CCManager is. Deze functiemanager wordt uitgezet en verstrekt het gebrek van gedrag.</li><li>Één eigenschapmanager die op heeft toegevoegd aan de naam van de eigenschapmanager, bijvoorbeeld, CCManagerOn. Deze functiemanager verstrekt steekproefcode voor de toegelaten eigenschap.</li></ul> |
| [com.adobe.primetime.reference.ui.catalog](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | Bevat UI-code voor de catalogus. |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | Bevat UI-code voor het logbestand. |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | Bevat UI-code voor de speler. |
| [com.adobe.primetime.reference.ui.settings](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | Bevat UI-code voor instellingen. |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | Bevat algemene hulpprogrammaklassen. |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | Bevat `HTTP-specific` hulpprogrammaklassen. |
