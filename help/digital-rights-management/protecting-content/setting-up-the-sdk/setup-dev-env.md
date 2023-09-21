---
description: Kopieer de bestanden van de dvd als u Primetime DRM wilt instellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Daarnaast moet u een certificaat aanvragen bij Adobe Systems, Incorporated. Adobe geeft u vervolgens meerdere referenties af waarmee u de integriteit van uw inhoud, licenties en communicatie tussen client en server in het pakket kunt beschermen.
title: De ontwikkelomgeving instellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# De ontwikkelomgeving instellen {#set-up-your-development-environment}

Kopieer de bestanden van de dvd als u Primetime DRM wilt instellen. Deze bestanden bevatten JAR-bestanden met code, certificaten en klassen van derden. Daarnaast moet u een certificaat aanvragen bij Adobe Systems, Incorporated. Adobe geeft u vervolgens meerdere referenties af waarmee u de integriteit van uw inhoud, licenties en communicatie tussen client en server in het pakket kunt beschermen.

Adobe biedt de Primetime DRM SDK op DVD:

1. Kopieer de volgende bestanden van [!DNL [DRM DVD]/SDK/] naar uw ontwikkelingssysteem (op uw Java-klassepad):

   * [!DNL adobe-flashaccess-certs.jar] - Bevat basiscertificaten voor Adobe
   * [!DNL adobe-flashaccess-sdk.jar] - Inclusief Primetime DRM Core SDK-klassen
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Inclusief Primetime DRM Professional SDK-klassen, alleen vereist voor Professional-functies

1. Kopieer de volgende bestanden van [!DNL [DRM DVD]/SDK/third-party] aan uw ontwikkelingssysteem:

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

1. (Optioneel) Voor functionaliteit met betrekking tot FMRMS (Adobe Flash Media Rights Management Server) 1.x-compatibiliteit, kopieert u `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` aan uw ontwikkelingssysteem:

   Implementeer dit alleen als u eerder FMRMS 1.x hebt geïmplementeerd en u de met FMRMS beveiligde inhoud niet opnieuw wilt verpakken. In dit geval moet u deze ondersteuning toevoegen aan uw licentieserver, zodat deze oude inhoud en clients kan beheren.
