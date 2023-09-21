---
description: De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.
title: Overzicht van Entitlement Manager
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Overzicht van Entitlement Manager {#entitlement-manager-overview}

De manager van de Entitlement is de eigenschapmanager die de implementatie van de authentificatie Primetime steunt.

## Overzicht van functies

De integratie van Primetime-verificatie met de Android Primetime SDK Reference Implementation voegt een nieuwe functiemanager toe aan de toepassing. Nochtans, in tegenstelling tot veel andere eigenschapmanagers, *de EntitlementManager wordt op verschillende plaatsen gebruikt door de toepassing*. Hieronder vindt u een overzicht van de wijzigingen en aanvullingen die zijn aangebracht in de Reference Implementation ter ondersteuning van Primetime-verificatie:

### EntitlementManager, klasse

De `EntitlementManager` De klasse handelt al mededeling met de authentificatie SDK van Primetime af, plus kapselt de toepassingslogica die voor de machtigingswerkschema&#39;s wordt vereist in. De `EntitlementManager`De openbare API van de toepassing wordt gebruikt om machtigingsworkflows te starten, terwijl de `EntitlementMangerListener` interface verstrekt een callback mechanisme voor de toepassing om te behandelen `EntitlementManger` gebeurtenissen.

### EntitlementManger callbacks

De belangrijkste activiteit van de Reference Implementation, de `CatalogActivity`, maakt een instantie van `EntitlementManagerListener` en registreert deze bij de `EntitlementManager`. Op die manier `EntitlementManager` kan de vereiste updates van UI aan de rest van de toepassing signaleren. De callbacks omvatten het tonen van/het verbergen van een ladingsdialoog, het tonen van statusdialogen, het bijwerken van toestemmings en authentificatiepictogrammen, en het beginnen van videoplayback op succesvolle vergunning.

### Machtigingsdialoogvensters

De `EntitlementDialogFragment` klasse genereert dialoogberichten op basis van de machtigingsstatus die aan de klasseconstructor is doorgegeven. Deze klasse wordt gebruikt voor berichten van het authentificatiesucces evenals alle foutenmeldingen. De `CatalogActivity` geeft de machtigingsdialoogvensters weer wanneer het specifieke gebeurtenissen ontvangt van de `EntitlementManager`. Bovendien `CatalogActivity` implementeert de `EntitlementDialogListener` interface, die callback methodes om omvat te signaleren wanneer een dialoog wordt gesloten of wanneer de gebruiker zich uit de dienst van de authentificatie Primetime afmeldt.

### Selectie en aanmelding van inhoudsprovider

Tijdens authentificatie met authentificatie Primetime, twee nieuwe activiteiten, `MvpdPickerActivity` en `MvpdLoginActivity`, stelt u de gebruiker in staat zijn inhoudprovider en aanmeldingsgegevens te selecteren. Beide activiteiten zijn gestart vanaf de `CatalogActivity` via de `EntitlementManager`. Bovendien worden beide `MvpdPickerActivity` en `MvpdLoginActivity` resultaten terugsturen naar de `CatalogActivity` en derhalve `CatalogActivity` moet de `Activity.onActivityResult` methode.

### Knop Aanmelden

De belangrijkste activiteit van de Reference Implementation, de `CatalogActivity`, bevat een nieuwe knop Aanmelden op de actiebalk. Met de knop Aanmelden kan de gebruiker verificatie starten met Primetime-verificatie. Bovendien kan de gebruiker verificatie starten door een beveiligde video te selecteren voor afspelen. Het pictogram en de tekst van de knop Aanmelden worden aangepast aan de verificatiestatus van de gebruiker en aan de `CatalogActivity` bevat code voor het bijwerken van het pictogram en de tekst van de knop wanneer de pagina wordt vernieuwd. Om dit te doen, wanneer `CatalogActivity` start, wordt aangeroepen `EntitlementManager.checkAuthentication()` de verificatiestatus van de gebruiker bijwerken.

### Inhoudsmachtiging

Binnen de `CatalogView`, worden nieuwe pictogrammen boven op het pictogram van de inhoud weergegeven om de autorisatiestatus van de gebruiker voor die inhoud aan te geven. Als de gebruiker bijvoorbeeld vooraf is geautoriseerd om een video te bekijken, wordt een groen cirkelpictogram weergegeven over de inhoud. Als de gebruiker echter niet vooraf is geautoriseerd om de video te bekijken, wordt een sleutelpictogram weergegeven. De weergave van deze pictogrammen wordt verwerkt in `ContentTileAdapter`, maar de actualisering van hun staat wordt gestart vanaf de `CatalogActivity` wanneer een callback in `EntitlementManagerListener` wordt aangeroepen.

### Inhoud afspelen

Voor het afspelen van video&#39;s is nu een machtigingscontrole door de `EntitlementManager`. De oproep tot `EntitlementManager.getAuthorization()` komt voor binnen `CatalogView`. Als de video autorisatie vereist en de gebruiker geautoriseerd is, wordt `PlayerActivity` wordt gestart vanaf de `CatalogActivity`.
