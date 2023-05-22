---
title: Gecodeerde bestandsinhoud controleren
description: Gecodeerde bestandsinhoud controleren
copied-description: true
exl-id: df1fd04d-016e-4770-bcb9-97bfe2d39260
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Gecodeerde bestandsinhoud controleren{#examining-encrypted-file-content}

U kunt de inhoud van een versleuteld mediabestand bekijken met behulp van de Java API.

Inhoud van gecodeerde bestanden controleren:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op. Zie *De SDK instellen* voor uw project.
1. Een `MediaEncrypter` -instantie.
1. Geef het gecodeerde bestand door aan de `MediaEncrypter.examineEncryptedContent` methode, die een `KeyMetaData` object.

1. Inspect de informatie in de `KeyMetaData` object.

Zie voor voorbeeldcode die beschrijft hoe u DRM-metagegevens uit een gecodeerd bestand kunt extraheren `com.adobe.flashaccess.samples.mediapackager.ExamineContent` in de opdrachtregelprogramma&#39;s voor de referentieimplementatie [!DNL samples/] directory.
