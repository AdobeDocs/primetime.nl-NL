---
description: De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.
seo-description: De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.
seo-title: Overzicht van Entitlement Manager
title: Overzicht van Entitlement Manager
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Overzicht van Entitlement Manager {#entitlement-manager-overview}

De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.

## Overzicht van functies

De integratie van Primetime-verificatie met de Android Primetime SDK Reference Implementation voegt een nieuwe functiemanager toe aan de toepassing. Nochtans, in tegenstelling tot vele andere eigenschapmanagers, *wordt EntitlementManager gebruikt in verscheidene plaatsen door de toepassing*. Hieronder vindt u een overzicht van de wijzigingen en aanvullingen die zijn aangebracht in de Reference Implementation ter ondersteuning van Primetime-verificatie:

### EntitlementManager, klasse

De klasse `EntitlementManager` handelt alle communicatie met de Primetime authentificatie SDK af, plus omvat de toepassingslogica die voor de machtigingswerkschema&#39;s wordt vereist. De openbare API van `EntitlementManager` wordt gebruikt door de toepassing om machtigingswerkschema&#39;s in werking te stellen, terwijl de `EntitlementMangerListener` interface een callback mechanisme voor de toepassing verstrekt om gebeurtenissen te behandelen `EntitlementManger`.

### EntitlementManger callbacks

De belangrijkste activiteit van de Implementatie van de Verwijzing, `CatalogActivity`, leidt tot een geval van `EntitlementManagerListener` en registreert het met `EntitlementManager`. Op deze manier geeft de `EntitlementManager` mogelijk de benodigde UI-updates door aan de rest van de toepassing. De callbacks omvatten het tonen van/het verbergen van een ladingsdialoog, het tonen van statusdialogen, het bijwerken van toestemmings en authentificatiepictogrammen, en het beginnen van videoplayback op succesvolle vergunning.

### Machtigingsdialoogvensters

De klasse `EntitlementDialogFragment` genereert dialoogberichten op basis van de machtigingsstatus die aan de klasseconstructor is doorgegeven. Deze klasse wordt gebruikt voor berichten van het authentificatiesucces evenals alle foutenmeldingen. `CatalogActivity` toont de machtigingsdialogen wanneer het specifieke gebeurtenissen van `EntitlementManager` ontvangt. Bovendien `CatalogActivity` voert `EntitlementDialogListener` interface uit, die callback methodes omvat om te signaleren wanneer een dialoog wordt gesloten of wanneer de gebruiker zich uit de dienst van de Authentificatie Primetime afmeldt.

### Selectie en aanmelding van inhoudsprovider

Tijdens verificatie met Primetime-verificatie kunnen de gebruiker met twee nieuwe activiteiten, `MvpdPickerActivity` en `MvpdLoginActivity`, zijn inhoudprovider en aanmelding selecteren. Beide activiteiten worden gestart vanaf `CatalogActivity` via `EntitlementManager`. Bovendien moeten zowel de `MvpdPickerActivity` als `MvpdLoginActivity` resultaten aan `CatalogActivity` en daarom `CatalogActivity` de `Activity.onActivityResult` methode met voeten treden.

### Knop Aanmelden

De hoofdactiviteit van de Referentie-implementatie, de `CatalogActivity`, bevat een nieuwe knop Aanmelden op de actiebalk. Met de knop Aanmelden kan de gebruiker verificatie starten met Primetime-verificatie. Bovendien kan de gebruiker verificatie starten door een beveiligde video te selecteren voor afspelen. Het pictogram van de knop Aanmelden en de tekst veranderen afhankelijk van de verificatiestatus van de gebruiker. De `CatalogActivity` bevat code waarmee het pictogram en de tekst van de knop worden bijgewerkt wanneer de pagina wordt vernieuwd. Om dit te doen, wanneer `CatalogActivity` begint, roept het `EntitlementManager.checkAuthentication()` om de de authentificatiestatus van de gebruiker bij te werken.

### Inhoudsmachtiging

Binnen `CatalogView`, worden de nieuwe pictogrammen getoond bovenop het pictogram van de inhoud om de de vergunningsstatus van de gebruiker voor die inhoud te signaleren. Als de gebruiker bijvoorbeeld vooraf is geautoriseerd om een video te bekijken, wordt een groen cirkelpictogram weergegeven over de inhoud. Als de gebruiker echter niet vooraf is geautoriseerd om de video te bekijken, wordt een sleutelpictogram weergegeven. De vertoning van deze pictogrammen wordt behandeld in `ContentTileAdapter`, nochtans wordt de update van hun staat in werking gesteld van `CatalogActivity` wanneer een callback in `EntitlementManagerListener` wordt geroepen.

### Inhoud afspelen

Voor het afspelen van video&#39;s is nu een machtigingscontrole van `EntitlementManager` vereist. De vraag aan `EntitlementManager.getAuthorization()` komt binnen `CatalogView` voor. Als de video toestemming vereist en de gebruiker wordt geautoriseerd, is `PlayerActivity` begonnen van `CatalogActivity`.

