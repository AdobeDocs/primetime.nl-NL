---
seo-title: Inhoud versleutelen
title: Inhoud versleutelen
uuid: ea71154e-557b-447e-bc14-208232f00be1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Inhoud versleutelen{#encrypting-content}

Bij het coderen van FLV- en F4V-inhoud wordt een `MediaEncrypter` object gebruikt. U kunt ook FLV- en F4V-bestanden verpakken die alleen audiotracks bevatten. Bij het coderen van H.264-inhoud voor eenvoudige apparaten kan het handig zijn om alleen gedeeltelijke codering toe te passen om de prestaties te verbeteren. In dergelijke gevallen kan een F4V-bestand gedeeltelijk worden gecodeerd met de `F4VDRMParameters.setVideoEncryptionLevel`methode.

Voer de volgende stappen uit om een FLV- of F4V-bestand te coderen met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in de ontwikkelomgeving van uw project.
1. Maak een `ServerCredential` instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `MediaEncrypter` instantie. Gebruik een bestand `MediaEncryperFactory` als u niet weet welk type bestand u hebt. Anders kunt u een `FLVEncrypter` of `F4VEncrypter` rechtstreeks maken.
1. Geef de versleutelingsopties op met behulp van een `DRMParameters` object.
1. Stel de handtekeningopties in met een `SignatureParameters` object en geef de `ServerCredential` instantie door aan de `setServerCredentials` methode.
1. Stel de sleutel- en licentiegegevens in met een `V2KeyParameters` object. Stel het beleid in met de `setPolicies` methode. Stel de informatie in die de client nodig heeft om contact op te nemen met de licentieserver door de `setLicenseServerUrl` en de `setLicenseServerTransportCertificate` methoden aan te roepen. Stel de CEK-coderingsopties in met de `setKeyProtectionOptions` methode en de aangepaste eigenschappen ervan met de `setCustomProperties` methode. Tot slot, afhankelijk van het gebruikte type van encryptie, gegoten het `DRMKeyParameters` voorwerp aan één van `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`, of `F4VDRMParameters`, en de encryptieopties plaatsen.
1. Codeer de inhoud door de invoer- en uitvoerbestanden en coderingsopties aan de `MediaEncrypter.encryptContent` methode door te geven.

Zie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s voor naslagimplementatie voor voorbeeldcode die aangeeft hoe inhoud moet worden gecodeerd.
