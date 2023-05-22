---
title: Inhoud versleutelen
description: Inhoud versleutelen
copied-description: true
exl-id: c6b5d8c7-eda4-40c0-a609-0ebfeba90c04
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Inhoud versleutelen{#encrypting-content}

U codeert video-inhoud met de `MediaEncrypter` object. U kunt mediabestanden versleutelen die alleen audiotracks bevatten. U kunt ook alleen gedeeltelijke versleuteling toepassen. bijvoorbeeld om de prestaties te verbeteren wanneer u H.264-inhoud codeert voor apparaten met een lagere kwaliteit.

Mediabestanden versleutelen met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die in *De ontwikkelomgeving instellen* in uw project.
1. Een `ServerCredential` -instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Een `MediaEncrypter` -instantie. Een `MediaEncryperFactory` als u niet weet welk type bestand u hebt.

1. Geef de versleutelingsopties op met een `DRMParameters` object.
1. Stel de handtekeningopties in met een `SignatureParameters` en geeft het `ServerCredential` instantie `setServerCredentials` methode.

1. De sleutel- en licentiegegevens instellen met behulp van een `V2KeyParameters` object. Het DRM-beleid instellen met de opdracht `setPolicies` methode. Stel de informatie in die de client nodig heeft om contact op te nemen met de licentieserver door de `setLicenseServerUrl` en `setLicenseServerTransportCertificate` methoden. Stel de CEK-coderingsopties in met de `setKeyProtectionOptions` en de bijbehorende aangepaste eigenschappen gebruiken `setCustomProperties` methode. Tot slot, afhankelijk van het gebruikte type van encryptie, giet `DRMKeyParameters` object naar het juiste type ( `VideoDRMParameters`, `AudioDRMParameters`) en stelt u de versleutelingsopties in.

1. Codeer de inhoud door de invoer- en uitvoerbestanden en versleutelingsopties aan de `MediaEncrypter.encryptContent` methode.

Voor voorbeeldcode die toont hoe te om inhoud te coderen, zie `com.adobe.flashaccess.samples.mediapackager.EncryptContent` in de opdrachtregelprogramma&#39;s voor de referentieimplementatie [!DNL samples/] directory.
