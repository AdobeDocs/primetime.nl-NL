---
title: Inhoud versleutelen
description: Inhoud versleutelen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Inhoud versleutelen{#encrypting-content}

U versleutelt video-inhoud met het object `MediaEncrypter`. U kunt mediabestanden versleutelen die alleen audiotracks bevatten. U kunt ook alleen gedeeltelijke versleuteling toepassen. bijvoorbeeld om de prestaties te verbeteren wanneer u H.264-inhoud codeert voor apparaten met een lagere kwaliteit.

Mediabestanden versleutelen met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in *De ontwikkelomgeving instellen* in uw project.
1. Maak een `ServerCredential`-instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `MediaEncrypter`-instantie. Gebruik een `MediaEncryperFactory` als u niet weet welk type bestand u hebt.

1. Geef de coderingsopties op met behulp van een `DRMParameters`-object.
1. Stel de handtekeningopties in met een `SignatureParameters`-object en geef de `ServerCredential`-instantie door aan de `setServerCredentials`-methode.

1. Stel de sleutel- en licentiegegevens in met behulp van een `V2KeyParameters`-object. Plaats het beleid DRM gebruikend de `setPolicies` methode. Stel de informatie in die de client nodig heeft om contact op te nemen met de licentieserver door de methoden `setLicenseServerUrl` en `setLicenseServerTransportCertificate` aan te roepen. Stel de CEK-coderingsopties in met de methode `setKeyProtectionOptions` en de aangepaste eigenschappen met de methode `setCustomProperties`. Tot slot, afhankelijk van het gebruikte type van encryptie, gegoten `DRMKeyParameters` voorwerp aan het aangewezen type ( `VideoDRMParameters`, `AudioDRMParameters`), en de encryptieopties plaatsen.

1. Codeer de inhoud door de invoer- en uitvoerbestanden en de versleutelingsopties aan de methode `MediaEncrypter.encryptContent` door te geven.

Zie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` in de map Reference Implementation Command Line Tools [!DNL samples/] voor voorbeeldcode die aangeeft hoe inhoud moet worden gecodeerd.
