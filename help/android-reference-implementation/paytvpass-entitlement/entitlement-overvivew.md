---
description: De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.
seo-description: De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.
seo-title: Overzicht van Entitlement Manager
title: Overzicht van Entitlement Manager
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Overzicht van Entitlement Manager {#entitlement-manager-overview}

De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.

## Overzicht van functies

De integratie van Primetime-verificatie met de Android Primetime SDK Reference Implementation voegt een nieuwe functiemanager toe aan de toepassing. Nochtans, in tegenstelling tot veel van andere eigenschapmanagers, wordt *EntitlementManager gebruikt in verscheidene plaatsen door de toepassing*. Hieronder vindt u een overzicht van de wijzigingen en aanvullingen die zijn aangebracht in de Reference Implementation ter ondersteuning van Primetime-verificatie:

### EntitlementManager, klasse

De `EntitlementManager` klasse handelt alle communicatie met de Primetime-verificatie-SDK af en kapselt de toepassingslogica in die voor de machtigingsworkflows is vereist. De openbare API `EntitlementManager`van de toepassing wordt gebruikt om machtigingswerkstromen in werking te stellen, terwijl de `EntitlementMangerListener` interface een callback mechanisme voor de toepassing verstrekt om `EntitlementManger` gebeurtenissen te behandelen.

### EntitlementManger callbacks

De hoofdactiviteit van de Reference Implementation, de `CatalogActivity`, maakt een instantie van `EntitlementManagerListener` en registreert deze bij de `EntitlementManager`. Op deze manier `EntitlementManager` kan de gebruiker de benodigde UI-updates naar de rest van de toepassing sturen. De callbacks omvatten het tonen van/het verbergen van een ladingsdialoog, het tonen van statusdialogen, het bijwerken van toestemmings en authentificatiepictogrammen, en het beginnen van videoplayback op succesvolle vergunning.

### Machtigingsdialoogvensters

De `EntitlementDialogFragment` klasse genereert dialoogberichten op basis van de machtigingsstatus die aan de klasseconstructor is doorgegeven. Deze klasse wordt gebruikt voor berichten van het authentificatiesucces evenals alle foutenmeldingen. De `CatalogActivity` machtigingsdialoogvensters worden weergegeven wanneer het specifieke gebeurtenissen van de `EntitlementManager`component ontvangt. Bovendien voert het `CatalogActivity` `EntitlementDialogListener` interface uit, die callback methodes omvat om te signaleren wanneer een dialoog wordt gesloten of wanneer de gebruiker zich uit de dienst van de authentificatie Primetime afmeldt.

### Selectie en aanmelding van inhoudsprovider

Tijdens authentificatie met authentificatie Primetime, twee nieuwe activiteiten, `MvpdPickerActivity` en `MvpdLoginActivity`, staan de gebruiker toe om hun inhoudsleverancier en login te selecteren. Beide activiteiten zijn van start gegaan vanuit de `CatalogActivity` via de `EntitlementManager`. Bovendien, zowel moeten de `MvpdPickerActivity` als `MvpdLoginActivity` terugkeerresultaten aan `CatalogActivity` en daarom `CatalogActivity` de `Activity.onActivityResult` methode met voeten treden.

### Knop Aanmelden

De hoofdactiviteit van de Reference Implementation, de `CatalogActivity`, bevat een nieuwe knop Aanmelden op de actiebalk. Met de knop Aanmelden kan de gebruiker verificatie starten met Primetime-verificatie. Bovendien kan de gebruiker verificatie starten door een beveiligde video te selecteren voor afspelen. Het pictogram en de tekst van de knop Aanmelden veranderen afhankelijk van de verificatiestatus van de gebruiker. De code `CatalogActivity` bevat code waarmee het pictogram en de tekst van de knop worden bijgewerkt wanneer de pagina wordt vernieuwd. Om dit te doen, wanneer het `CatalogActivity` begint, roept het `EntitlementManager.checkAuthentication()` om de de authentificatiestatus van de gebruiker bij te werken.

### Inhoudsmachtiging

In de `CatalogView`map worden nieuwe pictogrammen boven op het pictogram van de inhoud weergegeven om de machtigingsstatus van de gebruiker voor die inhoud aan te geven. Als de gebruiker bijvoorbeeld vooraf is geautoriseerd om een video te bekijken, wordt een groen cirkelpictogram weergegeven over de inhoud. Als de gebruiker echter niet vooraf is geautoriseerd om de video te bekijken, wordt een sleutelpictogram weergegeven. De vertoning van deze pictogrammen wordt behandeld binnen `ContentTileAdapter`, nochtans wordt de update van hun staat in werking gesteld van `CatalogActivity` wanneer een callback in `EntitlementManagerListener` wordt geroepen.

### Inhoud afspelen

Voor het afspelen van video&#39;s is nu een machtigingscontrole van de `EntitlementManager`gebruiker vereist. De vraag aan `EntitlementManager.getAuthorization()` komt binnen voor `CatalogView`. Als de video autorisatie vereist en de gebruiker geautoriseerd is, `PlayerActivity` wordt de video gestart vanaf de `CatalogActivity`.

