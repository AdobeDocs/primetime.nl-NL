---
description: Adobe biedt een Cloud DRM-service aan Adobe Primetime DRM-klanten die hun eigen Primetime DRM-licentieserver niet willen ontwikkelen en onderhouden. Door deze service te gebruiken, kunnen klanten de operationele en ontwikkelingscomplexiteit van DRM-licenties verminderen. Met Primetime Cloud DRM kunt u DRM-licenties verlenen voor alle apparaten die een videotoepassing kunnen uitvoeren die geschikt is voor TVSDK in de Primetime-browser, zoals iOS, Android, Desktops en Xbox360. Deze DRM-service wordt 24 uur per dag, 7 dagen per week, gehost en onderhouden door Adobe.
seo-description: Adobe biedt een Cloud DRM-service aan Adobe Primetime DRM-klanten die hun eigen Primetime DRM-licentieserver niet willen ontwikkelen en onderhouden. Door deze service te gebruiken, kunnen klanten de operationele en ontwikkelingscomplexiteit van DRM-licenties verminderen. Met Primetime Cloud DRM kunt u DRM-licenties verlenen voor alle apparaten die een videotoepassing kunnen uitvoeren die geschikt is voor TVSDK in de Primetime-browser, zoals iOS, Android, Desktops en Xbox360. Deze DRM-service wordt 24 uur per dag, 7 dagen per week, gehost en onderhouden door Adobe.
seo-title: Achtergrond
title: Achtergrond
uuid: 11a5b9ea-ebd2-47e0-b078-af2a3e1f7bf6
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Achtergrond {#background}

Adobe biedt een Cloud DRM-service aan Adobe Primetime DRM-klanten die hun eigen Primetime DRM-licentieserver niet willen ontwikkelen en onderhouden. Door deze service te gebruiken, kunnen klanten de operationele en ontwikkelingscomplexiteit van DRM-licenties verminderen. Met Primetime Cloud DRM kunt u DRM-licenties verlenen voor alle apparaten die een videotoepassing kunnen uitvoeren die geschikt is voor TVSDK in de Primetime-browser, zoals iOS, Android, Desktops en Xbox360. Deze DRM-service wordt 24 uur per dag, 7 dagen per week, gehost en onderhouden door Adobe.

>[!NOTE]
>
>Adobe Primetime DRM werd voorheen Adobe Access genoemd en daarvoor was Flash Access.

## Wat is inbegrepen bij Primetime Cloud DRM {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* Aangepaste verificatie-/machtigingsmodule en instructies voor het inschakelen van aangepaste verificatie voor uw inhoud. Raadpleeg de [!DNL Custom Authentication Entitlement] directory voor meer documentatie.
* Cloud DRM-specifiek licentieservercertificaat ( [!DNL .pem/.cer/.der])

* Cloud DRM-specific License Server Transport certificate ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* Voorbeeld-DRM-beleid voor verpakken

   * **policy_24hr** - het geheime voorgeheugen van vergunningen op schijf voor 24 uur. Na 24 uur moet een nieuwe licentie worden aangeschaft om de inhoud te kunnen bekijken. Alle andere beleidsregels in deze kit hebben ook een licentiecache van 24 uur.
   * **policy_ios_remotekeyserver** - Op iOS-apparaten wordt de DRM-licentie aangeschaft via Cloud DRM. Daarnaast zal de client alle AES-decoderingssleutels van Cloud DRM aanschaffen. Afspelen is niet toegestaan op iOS-apparaten met een handicap.

   * **policy_ios_localkeyserver** - Op iOS-apparaten wordt de DRM-licentie aangeschaft via Cloud DRM. Bovendien zal de client alle HLS AES-decoderingssleutels aanschaffen bij een lokale HTTP-server in plaats van Cloud DRM. Afspelen is niet toegestaan op iOS-apparaten met een handicap.

   * **policy_adobePass** - De client moet eerst worden geverifieerd met (voorheen Adobe Pass genoemd) anders wordt een licentie geweigerd.

* Het hulpmiddel van de Manager van het Beleid van Adobe om extra beleid te creëren DRM
* Voorbeeldvideo-inhoud voor verpakking

