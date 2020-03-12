---
seo-title: Certificaatupdates worden verwerkt wanneer uw door Adobe uitgegeven certificaten verlopen
title: Certificaatupdates worden verwerkt wanneer uw door Adobe uitgegeven certificaten verlopen
uuid: 5151ef15-daf6-4fb3-bf83-25ebac1d003b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Certificaatupdates worden verwerkt wanneer uw door Adobe uitgegeven certificaten verlopen {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire}

Het kan voorkomen dat u een nieuw certificaat moet ophalen van Adobe. Bijvoorbeeld, wanneer een productiecertificaat verloopt, verloopt een evaluatiecertificaat, of wanneer u van een evaluatie aan een productiecertificaat overschakelt. Wanneer een certificaat verloopt en u niet de inhoud wilt herverpakken die het oude certificaat gebruikte. U kunt de licentieserver bewust maken van zowel de oude als de nieuwe certificaten.

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

   In de verwijzingsimplementatie, zijn de eigenschappen u gebruikt `HandlerConfiguration.RevocationList` en `HandlerConfiguration.PolicyUpdateList`. Werk ook het certificaat bij dat wordt gebruikt om de handtekeningen te verifiëren: `RevocationList.verifySignature.X509Certificate`.

1. Om inhoud te verbruiken die met de oude certificaten werd verpakt, vereist de vergunningsserver de oude en nieuwe geloofsbrieven van de vergunningsserver en vervoergeloofsbrieven. Werk de licentieserver bij met de nieuwe en oude certificaten.

   Voor de referenties van de licentieserver:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de `LicenseHandler` constructor:

      * In de verwijzingsimplementatie, plaats het door het `LicenseHandler.ServerCredential` bezit.
      * In de Server van de Toegang van Adobe voor Beschermde Streaming, moet de huidige referentie de eerste geloofsbrieven zijn die in het `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier worden gespecificeerd.
   * Zorg ervoor dat de huidige en oude gegevens worden geleverd aan `AsymmetricKeyRetrieval`

      * In de verwijzingsimplementatie, plaats het door de `LicenseHandler.ServerCredential` en de `AsymmetricKeyRetrieval.ServerCredential. n` eigenschappen.
      * In de Server van de Toegang van Adobe voor Beschermde Streaming, worden de oude geloofsbrieven gespecificeerd na de eerste referentie in het `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier.
   Voor de vervoergeloofsbrieven:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de `HandlerConfiguration.setServerTransportCredential()` methode:

      * In de verwijzingsimplementatie, plaats het door het `HandlerConfiguration.ServerTransportCredential` bezit.
      * In de Adobe Access-server voor beveiligde streaming moet de huidige referentie de eerste referentie zijn die in het `TransportCredential` element in het bestand flashaccess-huurder.xml is opgegeven.
   * Zorg ervoor dat de oude gegevens worden doorgegeven aan `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * In de verwijzingsimplementatie, plaats het door de `HandlerConfiguration.AdditionalServerTransportCredential. n` eigenschappen.
      * In de Adobe Access-server voor beveiligde streaming wordt dit opgegeven na de eerste referentie in het `TransportCredential` element in het bestand flashaccess-huurder.xml.




1. Werk de verpakkingsgereedschappen bij om ervoor te zorgen dat ze inhoud verpakken met de huidige gegevens. Zorg ervoor dat het nieuwste certificaat van de licentieserver, het transportcertificaat en de referentie van de verpakker worden gebruikt voor het verpakken.
1. U kunt als volgt het licentieservercertificaat van de sleutelserver bijwerken:

   * Werk de gegevens bij in het configuratiebestand van de Adobe Access Key Server-gebruiker. Omvat zowel de oude als de nieuwe Belangrijke geloofsbrieven van de Server in flashaccess-keyserver-huurder.xml.
   * Zorg ervoor dat het huidige certificaat wordt doorgegeven aan de `HandlerConfiguration.setKeyServerCertificate()` methode.

      * In de verwijzingsimplementatie, plaats het door het `HandlerConfiguration.KeyServerCertificate` bezit.
      * In de Server van de Toegang van Adobe voor Beschermde Streaming, specificeer het certificaat van de Zeer belangrijke Server in door het het element van de Configuratie/van de Aannemer/Certificates/KeyServer.

