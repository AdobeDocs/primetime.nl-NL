---
seo-title: Gecodeerde bestandsinhoud controleren
title: Gecodeerde bestandsinhoud controleren
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Inhoud van gecodeerd bestand {#examining-encrypted-file-content} controleren

Voer de volgende stappen uit om de inhoud van een FLV- of F4V-bestand te controleren met behulp van de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in [De ontwikkelomgeving instellen](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in uw project.
1. Maak een `MediaEncrypter`-instantie.
1. Geef het gecodeerde bestand door aan de methode `MediaEncrypter.examineEncryptedContent`, die een object `KeyMetaData` retourneert.
1. Inspect de informatie binnen het `KeyMetaData` voorwerp.

Zie `com.adobe.flashaccess.samples.mediapackager.ExamineContent` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s voor naslagimplementatie voor voorbeeldcode die aangeeft hoe u DRM-metagegevens uit een gecodeerd bestand kunt extraheren.
