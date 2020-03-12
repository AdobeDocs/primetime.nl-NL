---
seo-title: Referenties opslaan
title: Referenties opslaan
uuid: a9e9db72-c921-4c28-ad1d-3fd3c2283f14
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Referenties opslaan{#storing-credentials}

De Primetime DRM SDK ondersteunt verschillende manieren om referenties op te slaan, zoals het gebruik van een Hardware Security Module (HSM) of als een PKCS12-bestand. De SDK gebruikt een referentie (openbare-sleutelcertificaat en de bijbehorende persoonlijke sleutel) wanneer de persoonlijke sleutel is vereist. De pakketsoftware gebruikt bijvoorbeeld een referentie om metagegevens te ondertekenen. De server van de Vergunning gebruikt een referentie om gegevens te decrypteren die met de Server van de Vergunning of de openbare sleutel van het Vervoer van het Vervoer zijn gecodeerd.

U moet de privésleutels zorgvuldig bewaken om de beveiliging van uw inhoud en licentieserver te garanderen. PKCS12 is een standaard archiefbestandsindeling voor het opslaan van referenties die met een wachtwoord zijn gecodeerd. (U kunt het PKCS12-bestand zelf ook versleutelen en ondertekenen.) De bestandsextensie [!DNL .pfx] wordt veel gebruikt voor bestanden die deze indeling ondersteunen.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Adobe raadt u aan een HSM te gebruiken voor maximale beveiliging.
>
>Zie de handleiding *Adobe Primetime DRM Secure Deployment Guidelines* .

>[!NOTE] {Important=&quot;high&quot;}
>
>Vanaf Java 1.7, steunt de Zon Java van 64 bits voor Vensters niet meer de interfaces PKCS11 die Primetime DRM voor communicatie met apparaten HSM vereist. Als u van plan bent om HSM te gebruiken, moet u een versie met 32 bits van Java gebruiken, of JDK gebruiken die de volledige interfaces PKCS11 steunt.

U kunt een persoonlijke sleutel op een HSM houden, en de Primetime DRM SDK gebruiken om in de referentie over te gaan u van HSM verkrijgt. Als u een referentie wilt gebruiken die op HSM wordt opgeslagen, moet u een leverancier JCE gebruiken die met HSM kan communiceren om een handvat aan de privé sleutel te krijgen. Vervolgens moet u de greep van de persoonlijke sleutel, de naam van de provider en het certificaat doorgeven waaraan de openbare sleutel is gekoppeld. `ServerCredentialFactory.getServerCredential()`

De SunPKCS11-provider vertegenwoordigt een voorbeeld van een JCE-provider die u kunt gebruiken om toegang te krijgen tot een persoonlijke sleutel op een HSM. Sommige HSM&#39;s worden ook opgenomen in een Java SDK die is gebundeld met een JCE-provider.

Raadpleeg de documentatie bij Sun Java voor instructies over het gebruik van deze provider.

PEM en DER zijn manieren om een openbare-sleutelcertificaat te coderen. PEM is een basis-64-codering en DER is een binaire codering. Certificaatbestanden gebruiken doorgaans de extensie [!DNL .cer], [!DNL .pem]of [!DNL .der]. Certificaten worden gebruikt wanneer alleen een openbare sleutel vereist is. Als voor een component alleen de openbare sleutel moet worden gebruikt, wordt u aangeraden dat onderdeel het certificaat te geven in plaats van een referentie- of PKCS12-bestand.
