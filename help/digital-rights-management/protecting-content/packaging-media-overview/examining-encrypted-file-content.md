---
seo-title: Gecodeerde bestandsinhoud controleren
title: Gecodeerde bestandsinhoud controleren
uuid: 1b3318f6-0850-43f2-9127-c72ea81a1bdf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gecodeerde bestandsinhoud controleren{#examining-encrypted-file-content}

U kunt de inhoud van een versleuteld mediabestand bekijken met behulp van de Java API.

Inhoud van gecodeerde bestanden controleren:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op. Zie De SDK *voor uw project* instellen.
1. Maak een `MediaEncrypter` instantie.
1. Geef het gecodeerde bestand door aan de `MediaEncrypter.examineEncryptedContent` methode die een `KeyMetaData` object retourneert.

1. Controleer de informatie in het `KeyMetaData` object.

Zie de `com.adobe.flashaccess.samples.mediapackager.ExamineContent` [!DNL samples/] map Reference Implementation Command Line Tools voor voorbeeldcode die beschrijft hoe u DRM-metagegevens kunt extraheren uit een gecodeerd bestand.
