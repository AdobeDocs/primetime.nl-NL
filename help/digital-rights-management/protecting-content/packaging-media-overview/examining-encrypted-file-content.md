---
title: Gecodeerde bestandsinhoud controleren
description: Gecodeerde bestandsinhoud controleren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Inhoud van versleuteld bestand controleren{#examining-encrypted-file-content}

U kunt de inhoud van een versleuteld mediabestand bekijken met behulp van de Java API.

Inhoud van gecodeerde bestanden controleren:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op. Zie *De SDK instellen* voor uw project.
1. Maak een `MediaEncrypter`-instantie.
1. Geef het gecodeerde bestand door aan de methode `MediaEncrypter.examineEncryptedContent`, die een object `KeyMetaData` retourneert.

1. Inspect de informatie binnen het `KeyMetaData` voorwerp.

Zie `com.adobe.flashaccess.samples.mediapackager.ExamineContent` in de map Reference Implementation Command Line Tools [!DNL samples/] voor voorbeeldcode die beschrijft hoe u DRM-metagegevens kunt extraheren uit een gecodeerd bestand.
