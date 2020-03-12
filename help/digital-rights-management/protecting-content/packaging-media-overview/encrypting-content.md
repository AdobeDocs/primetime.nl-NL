---
seo-title: Inhoud versleutelen
title: Inhoud versleutelen
uuid: 03f33473-bcd4-4e06-a823-e944897cb28e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Inhoud versleutelen{#encrypting-content}

U versleutelt video-inhoud met het `MediaEncrypter` object. U kunt mediabestanden versleutelen die alleen audiotracks bevatten. U kunt ook alleen gedeeltelijke versleuteling toepassen. bijvoorbeeld om de prestaties te verbeteren wanneer u H.264-inhoud codeert voor apparaten met een lagere kwaliteit.

Mediabestanden versleutelen met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die in de ontwikkelomgeving *van uw project worden* ingesteld.
1. Maak een `ServerCredential` instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `MediaEncrypter` instantie. Gebruik een bestand `MediaEncryperFactory` als u niet weet welk type bestand u hebt.

1. Geef de versleutelingsopties op met behulp van een `DRMParameters` object.
1. Stel de handtekeningopties in met een `SignatureParameters` object en geef de `ServerCredential` instantie door aan de `setServerCredentials` methode.

1. Stel de sleutel- en licentiegegevens in met een `V2KeyParameters` object. Stel het DRM-beleid in met de `setPolicies` methode. Stel de informatie in die de client nodig heeft om contact op te nemen met de licentieserver door de `setLicenseServerUrl` en de `setLicenseServerTransportCertificate` methoden aan te roepen. Stel de CEK-coderingsopties in met de `setKeyProtectionOptions` methode en de aangepaste eigenschappen ervan met de `setCustomProperties` methode. Tot slot, afhankelijk van het gebruikte type van encryptie, gegoten het `DRMKeyParameters` voorwerp aan het aangewezen type ( `VideoDRMParameters`, `AudioDRMParameters`), en de encryptieopties plaatsen.

1. Codeer de inhoud door de invoer- en uitvoerbestanden en coderingsopties aan de `MediaEncrypter.encryptContent` methode door te geven.

Zie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` [!DNL samples/] in de map Reference Implementation Command Line Tools voor voorbeeldcode die laat zien hoe inhoud kan worden gecodeerd.
