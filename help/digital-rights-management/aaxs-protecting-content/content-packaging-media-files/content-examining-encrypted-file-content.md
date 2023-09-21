---
title: Gecodeerde bestandsinhoud controleren
description: Gecodeerde bestandsinhoud controleren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Gecodeerde bestandsinhoud controleren {#examining-encrypted-file-content}

Voer de volgende stappen uit om de inhoud van een FLV- of F4V-bestand te controleren met behulp van de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in [De ontwikkelomgeving instellen](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in uw project.
1. Een `MediaEncrypter` -instantie.
1. Geef het gecodeerde bestand door aan de `MediaEncrypter.examineEncryptedContent` methode, die een `KeyMetaData` object.
1. Inspect de informatie in de `KeyMetaData` object.

Voor voorbeeldcode die aantoont hoe u DRM-metagegevens uit een gecodeerd bestand kunt extraheren, raadpleegt u `com.adobe.flashaccess.samples.mediapackager.ExamineContent` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.
