---
seo-title: Certificaatupdates worden verwerkt wanneer door Adobe uitgegeven certificaten verlopen
title: Certificaatupdates worden verwerkt wanneer door Adobe uitgegeven certificaten verlopen
uuid: abc0ca3e-a78f-4078-9480-7116843cce05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Certificaatupdates worden verwerkt wanneer door Adobe uitgegeven certificaten verlopen{#handling-certificate-updates-when-adobe-issued-certificates-expire}

Mogelijk moet u een nieuw certificaat aanvragen bij Adobe. Bijvoorbeeld, verloopt een productiecertificaat wanneer een evaluatiecertificaat verloopt of wanneer u van een evaluatie aan een productiecertificaat overschakelt. Wanneer een certificaat verloopt en u niet de inhoud wilt herverpakken die het oude certificaat gebruikt, kunt u de Server van de Vergunning van zowel de oude als nieuwe certificaten bewust maken.

Een server bijwerken met nieuwe certificaten:

1. (Optioneel) Wanneer u nieuwe vermeldingen toevoegt aan een bestaande DRM-lijst met beleidsupdates of -intrekkingen, moet u ondertekenen met de nieuwe referenties en het oude certificaat gebruiken om de handtekening op het bestaande bestand te valideren.

   U kunt bijvoorbeeld de volgende opdrachtregel gebruiken om een item toe te voegen aan een bestaande DRM-lijst met beleidsupdates die is ondertekend met een andere referentie:

   ```
   java -jar AdobePolicyUpdateListManager.jar newList -f oldList oldSigningCert.cer -u pol 0 "" ""
   ```

1. (Optioneel) Gebruik de Java API om de licentieserver bij te werken met de nieuwe DRM-lijst met beleidsupdates of intrekkingslijsten:

   ```
   HandlerConfiguration.setRevocationList() 
   ```

   of:

   ```
   HandlerConfiguration.setPolicyUpdateList()
   ```

   In de verwijzingsimplementatie, zijn de eigenschappen die u gebruikt `HandlerConfiguration.RevocationList` en `HandlerConfiguration.PolicyUpdateList`. U moet ook het certificaat bijwerken waarmee de handtekeningen worden geverifieerd: `RevocationList.verifySignature.X509Certificate`.

1. Werk de licentieserver bij met de nieuwe en oude certificaten.

   Als u inhoud wilt verbruiken die met de oude certificaten is verpakt, zorg ervoor dat de vergunningsserver toegang tot de oude en nieuwe geloofsbrieven van de vergunningsserver evenals vervoergeloofsbrieven heeft.

   Voor de referenties van de licentieserver:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de `LicenseHandler` constructor:

      * In de verwijzingsimplementatie, plaats het met het `LicenseHandler.ServerCredential` bezit.
      * In de Adobe Primetime DRM Server voor Beschermde Streaming, moet de huidige referentie de eerste referentie zijn die in het `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier wordt gespecificeerd.
   * Zorg ervoor dat de huidige en oude gegevens worden geleverd aan `AsymmetricKeyRetrieval`

      * In de verwijzingsimplementatie, plaats het met de `LicenseHandler.ServerCredential` en `AsymmetricKeyRetrieval.ServerCredential. n` eigenschappen.

      * In de Server Primetime DRM voor Beschermde Streaming, worden de oude geloofsbrieven gespecificeerd na de eerste referentie in het `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier.
   Voor de vervoergeloofsbrieven:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de `HandlerConfiguration.setServerTransportCredential()` methode:

      * In de verwijzingsimplementatie, plaats het met het `HandlerConfiguration.ServerTransportCredential` bezit.
      * In de Primetime DRM-server voor beveiligde streaming moet de huidige referentie de eerste referentie zijn die in het `TransportCredential` element in het [!DNL flashaccess-tenant.xml] bestand is opgegeven.
   * Zorg ervoor dat de oude gegevens worden doorgegeven aan `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * In de verwijzingsimplementatie, plaats het met de `HandlerConfiguration.AdditionalServerTransportCredential. n` eigenschappen.
      * In de Server Primetime DRM voor beschermde het stromen, wordt dit gespecificeerd na de eerste referentie in het `TransportCredential` element in het flashaccess-huurder.xml- dossier.




1. Werk de verpakkingsgereedschappen bij om ervoor te zorgen dat ze inhoud verpakken met de huidige gegevens. Zorg ervoor dat het nieuwste certificaat van de licentieserver, het transportcertificaat en de referentie van de verpakker worden gebruikt voor het verpakken.
1. Werk het certificaat van de Server van de Vergunning van de Sleutelserver als volgt bij:

   * Werk de geloofsbrieven in het dossier van de de huurdersconfiguratie van de Server van de Server van de Sleutel van Adobe bij Primetime DRM door zowel de oude als nieuwe geloofsbrieven van de Server in flashaccess-keyserver-huurder.xml te omvatten.
   * Zorg ervoor dat het huidige certificaat wordt doorgegeven aan de `HandlerConfiguration.setKeyServerCertificate()` methode.

      * In de verwijzingsimplementatie, plaats het met het `HandlerConfiguration.KeyServerCertificate` bezit.
      * In de Server Primetime DRM voor Beschermde Streaming, specificeer het certificaat van de Zeer belangrijke Server in door het element van de Configuratie/van de Aannemer/Certificates/KeyServer.

