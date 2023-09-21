---
title: Inhoud versleutelen
description: Inhoud versleutelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Inhoud versleutelen{#encrypting-content}

Bij het coderen van FLV- en F4V-inhoud moet een `MediaEncrypter` object. U kunt ook FLV- en F4V-bestanden verpakken die alleen audiotracks bevatten. Bij het coderen van H.264-inhoud voor eenvoudige apparaten kan het handig zijn om alleen gedeeltelijke codering toe te passen om de prestaties te verbeteren. In dergelijke gevallen kan een F4V-bestand gedeeltelijk worden gecodeerd met het `F4VDRMParameters.setVideoEncryptionLevel`methode.

Voer de volgende stappen uit om een FLV- of F4V-bestand te coderen met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in de ontwikkelomgeving van uw project.
1. Een `ServerCredential` -instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Een `MediaEncrypter` -instantie. Een `MediaEncryperFactory` als u niet weet welk type bestand u hebt. Anders kunt u een `FLVEncrypter` of `F4VEncrypter` rechtstreeks.
1. Geef de versleutelingsopties op met behulp van een `DRMParameters` object.
1. Stel de handtekeningopties in met een `SignatureParameters` en geeft het `ServerCredential` van het `setServerCredentials` methode.
1. De sleutel- en licentiegegevens instellen met behulp van een `V2KeyParameters` object. Beleid instellen met de opdracht `setPolicies` methode. Stel de informatie in die de client nodig heeft om contact op te nemen met de licentieserver door de `setLicenseServerUrl` en `setLicenseServerTransportCertificate` methoden. Stel de CEK-coderingsopties in met de `setKeyProtectionOptions` en de bijbehorende aangepaste eigenschappen gebruiken `setCustomProperties` methode. Tot slot, afhankelijk van het gebruikte type van encryptie, giet `DRMKeyParameters` object naar een van `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`, of `F4VDRMParameters`en stelt u de versleutelingsopties in.
1. Codeer de inhoud door de invoer- en uitvoerbestanden en versleutelingsopties aan de `MediaEncrypter.encryptContent` methode.

Voor voorbeeldcode die aantoont hoe inhoud te coderen, zie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.
