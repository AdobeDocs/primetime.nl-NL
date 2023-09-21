---
description: Adobe biedt een Cloud DRM-service aan Adobe Primetime DRM-klanten die hun eigen Primetime DRM-licentieserver niet willen ontwikkelen en onderhouden. Door deze service te gebruiken, kunnen klanten de operationele en ontwikkelingscomplexiteit van DRM-licenties verminderen. Met Primetime Cloud DRM kunt u DRM-licenties verlenen voor alle apparaten die een videotoepassing kunnen uitvoeren die geschikt is voor TVSDK in de primaire browser, zoals iOS, Android, Desktops en Xbox360. Deze DRM-service wordt gehost en onderhouden door de Adobe, met 24/7 uptime.
title: Achtergrond
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Achtergrond {#background}

Adobe biedt een Cloud DRM-service aan Adobe Primetime DRM-klanten die hun eigen Primetime DRM-licentieserver niet willen ontwikkelen en onderhouden. Door deze service te gebruiken, kunnen klanten de operationele en ontwikkelingscomplexiteit van DRM-licenties verminderen. Met Primetime Cloud DRM kunt u DRM-licenties verlenen voor alle apparaten die een videotoepassing kunnen uitvoeren die geschikt is voor TVSDK in de primaire browser, zoals iOS, Android, Desktops en Xbox360. Deze DRM-service wordt gehost en onderhouden door de Adobe, met 24/7 uptime.

>[!NOTE]
>
>Adobe Primetime DRM werd vroeger genoemd Toegang van de Adobe, en voorafgaand aan dat, Flash Access.

## Wat is inbegrepen bij Primetime Cloud DRM {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Aangepaste verificatie-/machtigingsmodule en instructies voor het inschakelen van aangepaste verificatie voor uw inhoud. Raadpleeg voor meer documentatie de [!DNL Custom Authentication Entitlement] directory.
* Cloud DRM-specifiek licentieservercertificaat ( [!DNL .pem/.cer/.der])

* Cloud DRM-specifiek Vervoerscertificaat voor licentieserver ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Voorbeeld-DRM-beleid voor verpakken

   * **policy_24hr** - Licenties zijn 24 uur lang in cache opgeslagen. Na 24 uur moet een nieuwe licentie worden aangeschaft om de inhoud te kunnen bekijken. Alle andere beleidsregels in deze kit hebben ook een licentiecache van 24 uur.
   * **policy_ios_remotekeyserver** - Op iOS-apparaten wordt de DRM-licentie aangeschaft via Cloud DRM. Daarnaast zal de client alle AES-decoderingssleutels van Cloud DRM aanschaffen. Afspelen is niet toegestaan op iOS-apparaten die op de gevangenis zijn afgebroken.

   * **policy_ios_localkeyserver** - Op iOS-apparaten wordt de DRM-licentie aangeschaft via Cloud DRM. Bovendien zal de client alle HLS AES-decoderingssleutels aanschaffen bij een lokale HTTP-server in plaats van Cloud DRM. Afspelen is niet toegestaan op iOS-apparaten die op de gevangenis zijn afgebroken.

   * **policy_adobePass** - De client moet eerst worden geverifieerd met (voorheen Adobe Pass genoemd), anders wordt een licentie geweigerd.

* Het hulpmiddel van de Manager van het Beleid van de Adobe om extra beleid te creëren DRM
* Voorbeeldvideo-inhoud voor verpakking
