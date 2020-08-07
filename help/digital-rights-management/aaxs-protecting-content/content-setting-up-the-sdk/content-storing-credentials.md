---
seo-title: Referenties opslaan
title: Referenties opslaan
uuid: dbce523c-32d9-423f-bc95-39786f85fc29
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Referenties opslaan{#storing-credentials}

De SDK ondersteunt meerdere manieren om referenties op te slaan (een openbare-sleutelcertificaat en de bijbehorende persoonlijke sleutel), inclusief op een HSM- of PKCS12-bestand. De geloofsbrieven worden gebruikt wanneer de privé sleutel wordt vereist (bijvoorbeeld, voor de verpakker om de meta-gegevens te ondertekenen, of voor de Server van de Vergunning om gegevens te decrypteren die met de Server van de Vergunning of de openbare sleutel van het Vervoer worden gecodeerd). De privé sleutels moeten zorgvuldig worden bewaakt om de veiligheid van uw inhoud en de Server van de Vergunning te verzekeren. PKCS12 is een standaardindeling voor een bestand dat een referentie bevat die met een wachtwoord is gecodeerd. De bestandsextensie .pfx wordt veel gebruikt voor bestanden met deze indeling.

>[!NOTE]
>
>Adobe raadt aan een HSM te gebruiken voor maximale beveiliging. Voor meer informatie, zie de Veilige Richtlijnen van de Plaatsing van de Toegang van de Adobe.

>[!NOTE]
>
>Vanaf Java1.7, steunt 64bit Zon Java voor Vensters niet de interfaces PKCS11 die Adobe Access DRM vereist om met apparaten te communiceren HSM. Als u een HSM wilt gebruiken, moet u een 32-bits versie van Java gebruiken of een JDK gebruiken die de volledige PKCS11-interfaces ondersteunt.

U kunt een privé sleutel op een Module van de Veiligheid van de Hardware (HSM) houden en SDK gebruiken om in de referentie over te gaan u van HSM verkrijgt. Als u een referentie wilt gebruiken die op een HSM is opgeslagen, gebruikt u een JCE-provider die met een HSM kan communiceren om een greep naar de persoonlijke sleutel te krijgen. Geef vervolgens de greep van de persoonlijke sleutel, de naam van de provider en het certificaat met de openbare sleutel door aan `ServerCredentialFactory.getServerCredential()`.

De SunPKCS11-provider is een voorbeeld van een JCE-provider die kan worden gebruikt voor toegang tot een persoonlijke sleutel op een HSM (zie de Sun Java-documentatie voor instructies over het gebruik van deze provider). Sommige HSM&#39;s worden ook geleverd met een Java SDK die een JCE-provider bevat.

PEM en DER zijn twee manieren om een openbare-sleutelcertificaat te coderen. PEM is een basis-64-codering en DER is een binaire codering. Certificaatbestanden gebruiken doorgaans de extensie .cer, .pem. of .der. Certificaten worden gebruikt op plaatsen waar alleen de openbare sleutel vereist is. Als voor een component alleen de openbare sleutel moet worden gebruikt, is het beter om die component het certificaat te verschaffen in plaats van een referentie- of PKCS12-bestand.
