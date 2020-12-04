---
description: Kopieer de bestanden van de dvd als u Primetime DRM wilt instellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Daarnaast moet u een certificaat aanvragen bij Adobe Systems, Incorporated. Vervolgens geeft Adobe u meerdere referenties uit waarmee u de integriteit van uw inhoud, licenties en communicatie tussen client en server in het pakket kunt beschermen.
seo-description: Kopieer de bestanden van de dvd als u Primetime DRM wilt instellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Daarnaast moet u een certificaat aanvragen bij Adobe Systems, Incorporated. Vervolgens geeft Adobe u meerdere referenties uit waarmee u de integriteit van uw inhoud, licenties en communicatie tussen client en server in het pakket kunt beschermen.
seo-title: De ontwikkelomgeving instellen
title: De ontwikkelomgeving instellen
uuid: 68afefe8-7ec6-466e-89a8-bc0da8afb4c8
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# De ontwikkelomgeving instellen {#set-up-your-development-environment}

Kopieer de bestanden van de dvd als u Primetime DRM wilt instellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Daarnaast moet u een certificaat aanvragen bij Adobe Systems, Incorporated. Vervolgens geeft Adobe u meerdere referenties uit waarmee u de integriteit van uw inhoud, licenties en communicatie tussen client en server in het pakket kunt beschermen.

Adobe biedt de Primetime DRM SDK op DVD:

1. Kopieer de volgende bestanden van [!DNL [DRM DVD]/SDK/] naar uw ontwikkelingssysteem (op uw Java-klassenpad):

   * [!DNL adobe-flashaccess-certs.jar] - Bevat Adobe-basiscertificaten
   * [!DNL adobe-flashaccess-sdk.jar] - Inclusief Primetime DRM Core SDK-klassen
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Inclusief Primetime DRM Professional SDK-klassen, alleen vereist voor Professional-functies

1. Kopieer de volgende bestanden van [!DNL [DRM DVD]/SDK/thirdparty] naar uw ontwikkelingssysteem:

   * [!DNL bcmail-jdk15-141.jar]
   * [!DNL bcprov-jdk15-141.jar]
   * [!DNL commons-discovery-0.4.jar]
   * [!DNL commons-logging-1.1.1.jar]
   * [!DNL cryptoj.jar]
   * [!DNL jaxb-api.jar]
   * [!DNL jaxb-impl.jar]
   * [!DNL jaxb-libs.jar]
   * [!DNL relaxngDatatype.jar]
   * [!DNL rm-pdrl.jar]
   * [!DNL xsdlib.jar]
   * [!DNL jackson-annotations-2.4.0-rc4-20140522.175222-3.jar]
   * [!DNL jackson-core--2.4.0-rc4-20140529.184520-13.jar]
   * [!DNL jackson-databind-2.4.0-rc4-20140603.005043-38.jar]

1. (Optioneel) Voor betere prestaties kunt u native ondersteuning voor cryptografische bewerkingen inschakelen door de juiste platformspecifieke bibliotheek te kopiëren van [!DNL [DRM DVD]/SDK/third-party/cryptoj/] naar uw ontwikkelingssysteem (vergeet niet de locatie op uw pad te plaatsen):

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

      >[!NOTE]
      >
      >32-bits en 64-bits versies van deze bibliotheken zijn beschikbaar. Gebruik de 64-bits versie alleen als u een 64-bits besturingssysteem hebt en de 64-bits versie van Java uitvoert.

1. (Optioneel) Voor functionaliteit die gerelateerd is aan de compatibiliteit met FMRMS (Adobe Flash Media Rights Management Server) 1.x, kopieert u `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` naar uw ontwikkelingssysteem:

   Implementeer dit alleen als u eerder FMRMS 1.x hebt geïmplementeerd en u de met FMRMS beveiligde inhoud niet opnieuw wilt verpakken. In dit geval moet u deze ondersteuning toevoegen aan uw licentieserver, zodat deze oude inhoud en clients kan beheren.
