---
title: Certificaatupdates verwerken wanneer uw door Adobe uitgegeven certificaten verlopen
description: Certificaatupdates verwerken wanneer uw door Adobe uitgegeven certificaten verlopen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Certificaatupdates verwerken wanneer uw door Adobe uitgegeven certificaten verlopen {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Het kan gebeuren dat u een nieuw certificaat moet ophalen uit de Adobe. Bijvoorbeeld, wanneer een productiecertificaat verloopt, verloopt een evaluatiecertificaat, of wanneer u van een evaluatie aan een productiecertificaat overschakelt. Wanneer een certificaat verloopt en u niet de inhoud wilt herverpakken die het oude certificaat gebruikte. U kunt de licentieserver bewust maken van zowel de oude als de nieuwe certificaten.

Gebruik de volgende procedure om uw server bij te werken met de nieuwe certificaten:

1. (Optioneel) Wanneer u nieuwe vermeldingen toevoegt aan een bestaande lijst met beleidsupdates of intrekkingen, moet u zich met de nieuwe referenties aanmelden en de handtekening op het bestaande bestand valideren met het oude certificaat.

   Gebruik bijvoorbeeld de volgende opdrachtregel om een item toe te voegen aan een bestaande lijst met beleidsupdates die is ondertekend met een andere referentie:

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. Gebruik de Java API om de licentieserver bij te werken met de nieuwe lijst met beleidsupdates of intrekkingslijsten:

   ```
    HandlerConfiguration.setRevocationList() 
   ```

   of:

   ```
    HandlerConfiguration.setPolicyUpdateList()
   ```

   In de voorbeeldimplementatie zijn de eigenschappen die u gebruikt `HandlerConfiguration.RevocationList` en `HandlerConfiguration.PolicyUpdateList`. Werk ook het certificaat bij dat wordt gebruikt om de handtekeningen te verifiëren: `RevocationList.verifySignature.X509Certificate`.

1. Om inhoud te verbruiken die met de oude certificaten werd verpakt, vereist de vergunningsserver de oude en nieuwe geloofsbrieven van de vergunningsserver en vervoergeloofsbrieven. Werk de licentieserver bij met de nieuwe en oude certificaten.

   Voor de referenties van de licentieserver:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de `LicenseHandler` constructor:

      * In de verwijzingsimplementatie plaatst het door `LicenseHandler.ServerCredential` eigenschap.
      * In de Adobe Access Server for Protected Streaming moet de huidige referentie de eerste referentie zijn die is opgegeven in het dialoogvenster `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier.

   * Zorg ervoor dat de huidige en oude gegevens worden geleverd aan `AsymmetricKeyRetrieval`

      * In de verwijzingsimplementatie plaatst het door `LicenseHandler.ServerCredential` en `AsymmetricKeyRetrieval.ServerCredential. n` eigenschappen.
      * In de Adobe Access Server for Protected Streaming worden de oude referenties opgegeven na de eerste referentie in het dialoogvenster `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier.

   Voor de vervoersgegevens:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de `HandlerConfiguration.setServerTransportCredential()` methode:

      * In de verwijzingsimplementatie plaatst het door `HandlerConfiguration.ServerTransportCredential` eigenschap.
      * In de Adobe Access Server voor beveiligde streaming moet de huidige referentie de eerste referentie zijn die is opgegeven in het dialoogvenster `TransportCredential` element in het flashaccess-huurder.xml- dossier.

   * Zorg ervoor dat de oude gegevens worden geleverd aan `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * In de verwijzingsimplementatie plaatst het door `HandlerConfiguration.AdditionalServerTransportCredential. n` eigenschappen.
      * In de Adobe Access Server voor beveiligde streaming wordt dit opgegeven na de eerste referentie in het dialoogvenster `TransportCredential` element in het flashaccess-huurder.xml- dossier.

1. Werk de verpakkingsgereedschappen bij om ervoor te zorgen dat ze inhoud verpakken met de huidige gegevens. Zorg ervoor dat het nieuwste certificaat van de licentieserver, het transportcertificaat en de referentie van de verpakker worden gebruikt voor het verpakken.
1. U kunt als volgt het licentieservercertificaat van de sleutelserver bijwerken:

   * Werk de geloofsbrieven in het de configuratiedossier van de Server van de Toegang van de Toegang van de Adobe Zeer belangrijke bij. Omvat zowel de oude als de nieuwe Belangrijke geloofsbrieven van de Server in flashaccess-keyserver-huurder.xml.
   * Zorg ervoor dat het huidige certificaat wordt doorgegeven aan de `HandlerConfiguration.setKeyServerCertificate()` methode.

      * In de verwijzingsimplementatie plaatst het door `HandlerConfiguration.KeyServerCertificate` eigenschap.
      * In Adobe Access Server voor Beschermde Streaming, specificeer het certificaat van de Server van de Sleutel in door het configuratie/Aannemer/Certificates/KeyServer element.
