---
title: Toegang tot de Android SDK Single Sign-On (SSO) voor Android 10-apps
description: Toegang tot de Android SDK Single Sign-On (SSO) voor Android 10-apps
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---



# Toegang tot de Android SDK Single Sign-On (SSO) voor Android 10-apps {#access-enabler-android-sdk-single-sign-on-sso-on-android-10-apps}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Overzicht

Single Sign-On (SSO) tussen op Adobe Primetime-verificatie gebaseerde apps is beschikbaar op apparaten die Android OS gebruiken via de Access Enabler Android SDK. Om Single Sign-On (SSO) aan te bieden op Android-apparaten, maken de Access Enabler Android SDK versie 3.2.1 (nieuwste versie) en eerdere versies gebruik van een gedeeld databasebestand dat is opgeslagen in een Android-opslagimplementatie en dat toegankelijk is voor alle Adobe Primetime-verificatie-apps.

Google in de meest recente Android-release van 10 heeft echter enkele wijzigingen aangebracht &quot;om gebruikers meer controle over hun bestanden te geven en het bestand overzichtelijker te maken, krijgen toepassingen die gericht zijn op Android 10 (API-niveau 29) en hoger standaard bereiktoegang tot een extern opslagapparaat, ofwel bereikopslag. Dergelijke apps kunnen alleen hun toepassingsspecifieke map zien `\[...\]`&quot;. Meer informatie over deze wijzigingen in de Android 10-opslag vindt u in [Documentatie voor gegevens- en bestandsopslag voor Android](https://developer.android.com/training/data-storage/files/external-scoped).

Als gevolg van deze wijzigingen wordt de Single Sign-On (SSO) aangeboden door Access Enabler Android-versie **3.2.1 SDK (nieuwste)** en eerdere versies kunnen worden beïnvloed op Android 10-apparaten, zoals wordt beschreven in de volgende sectie.

Zie [Overzicht van Roku SSO](/help/authentication/roku-sso-overview.md).

## Gedrag

Afhankelijk van de **doel-SDK-niveau** of het gebruik van **android:requestLegacyExternalStorage** Manier attribuut Single Sign-On (SSO) die door Access Enabler Android versie 3.2.1 SDK (recentste) wordt aangeboden en de vorige versies zullen zich momenteel als volgt gedragen:

- Uw app-doelen **Android 9 (API-niveau 28)** of lager **-\>** Single Sign-On (SSO) **zal werken**
- Uw app-doelen **Android 10** **(API-niveau 29)** en doet **set** de waarde van **requestLegacyExternalStorage instellen op true** in het manifestbestand van uw app **-\>** Single Sign-On (SSO) **zal werken**
- Uw app-doelen **Android 10** **(API-niveau 29)** en doet **niet ingesteld** de waarde van **requestLegacyExternalStorage instellen op true** in het manifestbestand van uw app **-\>** Single Sign-On (SSO) **werkt niet**


>[!TIP]
>
> Voordat de Adobe Primetime-verificatietoegang Access Enabler Android-SDK volledig compatibel is met opslag met bereik, kunt u tijdelijk weigeren op basis van het doel-SDK-niveau van uw app of het requestLegacyExternalStorage-manifestelement, zoals in het openbaar wordt uitgelegd [Android-documentatie](https://developer.android.com/training/data-storage/files/external-scoped#opt-out-of-scoped-storage).

