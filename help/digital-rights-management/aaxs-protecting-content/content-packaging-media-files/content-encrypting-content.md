---
seo-title: Inhoud versleutelen
title: Inhoud versleutelen
uuid: ea71154e-557b-447e-bc14-208232f00be1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Inhoud versleutelen{#encrypting-content}

Bij het coderen van FLV- en F4V-inhoud wordt een `MediaEncrypter`-object gebruikt. U kunt ook FLV- en F4V-bestanden verpakken die alleen audiotracks bevatten. Bij het coderen van H.264-inhoud voor eenvoudige apparaten kan het handig zijn om alleen gedeeltelijke codering toe te passen om de prestaties te verbeteren. In dergelijke gevallen kan een F4V-bestand gedeeltelijk worden gecodeerd met de methode `F4VDRMParameters.setVideoEncryptionLevel`.

Voer de volgende stappen uit om een FLV- of F4V-bestand te coderen met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in de ontwikkelomgeving van uw project.
1. Maak een `ServerCredential`-instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `MediaEncrypter`-instantie. Gebruik een `MediaEncryperFactory` als u niet weet welk type bestand u hebt. Anders kunt u een `FLVEncrypter` of `F4VEncrypter` direct tot stand brengen.
1. Geef de coderingsopties op met behulp van een `DRMParameters`-object.
1. Stel de handtekeningopties in met een `SignatureParameters`-object en geef de `ServerCredential`-instantie door aan de `setServerCredentials`-methode.
1. Stel de sleutel- en licentiegegevens in met behulp van een `V2KeyParameters`-object. Stel het beleid in met de methode `setPolicies`. Stel de informatie in die de client nodig heeft om contact op te nemen met de licentieserver door de methoden `setLicenseServerUrl` en `setLicenseServerTransportCertificate` aan te roepen. Stel de CEK-coderingsopties in met de methode `setKeyProtectionOptions` en de aangepaste eigenschappen met de methode `setCustomProperties`. Ten slotte, afhankelijk van het gebruikte type van encryptie, giet het `DRMKeyParameters` voorwerp aan één van `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`, of `F4VDRMParameters`, en de encryptieopties plaatsen.
1. Codeer de inhoud door de invoer- en uitvoerbestanden en de versleutelingsopties aan de methode `MediaEncrypter.encryptContent` door te geven.

Zie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie voor voorbeeldcode die aangeeft hoe inhoud moet worden gecodeerd.
