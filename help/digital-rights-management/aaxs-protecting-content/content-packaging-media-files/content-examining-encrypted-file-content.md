---
seo-title: Gecodeerde bestandsinhoud controleren
title: Gecodeerde bestandsinhoud controleren
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gecodeerde bestandsinhoud controleren {#examining-encrypted-file-content}

Voer de volgende stappen uit om de inhoud van een FLV- of F4V-bestand te controleren met behulp van de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die in de ontwikkelomgeving [van uw project worden](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) ingesteld.
1. Maak een `MediaEncrypter` instantie.
1. Geef het gecodeerde bestand door aan de `MediaEncrypter.examineEncryptedContent` methode die een `KeyMetaData` object retourneert.
1. Controleer de informatie in het `KeyMetaData` object.

Zie `com.adobe.flashaccess.samples.mediapackager.ExamineContent` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s voor naslagimplementatie voor voorbeeldcode die aangeeft hoe u DRM-metagegevens uit een gecodeerd bestand kunt extraheren.
