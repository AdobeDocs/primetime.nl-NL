---
seo-title: Certificaatupdates worden verwerkt wanneer uw door Adobe uitgegeven certificaten verlopen
title: Certificaatupdates worden verwerkt wanneer uw door Adobe uitgegeven certificaten verlopen
uuid: 5151ef15-daf6-4fb3-bf83-25ebac1d003b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---


# Certificaatupdates verwerken wanneer uw door Adobe uitgegeven certificaten {#handling-certificate-updates-when-your-adobe-issued-certifcates-expire} verlopen

Er kunnen momenten zijn waarop u een nieuw certificaat van Adobe moet ophalen. Bijvoorbeeld, wanneer een productiecertificaat verloopt, verloopt een evaluatiecertificaat, of wanneer u van een evaluatie aan een productiecertificaat overschakelt. Wanneer een certificaat verloopt en u niet de inhoud wilt herverpakken die het oude certificaat gebruikte. U kunt de licentieserver bewust maken van zowel de oude als de nieuwe certificaten.

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

   In de verwijzingsimplementatie, zijn de eigenschappen u `HandlerConfiguration.RevocationList` en `HandlerConfiguration.PolicyUpdateList` gebruikt. Werk ook het certificaat bij dat wordt gebruikt om de handtekeningen te verifiëren: `RevocationList.verifySignature.X509Certificate`.

1. Om inhoud te verbruiken die met de oude certificaten werd verpakt, vereist de vergunningsserver de oude en nieuwe geloofsbrieven van de vergunningsserver en vervoergeloofsbrieven. Werk de licentieserver bij met de nieuwe en oude certificaten.

   Voor de referenties van de licentieserver:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de constructor `LicenseHandler`:

      * In de verwijzingsimplementatie, plaats het door het `LicenseHandler.ServerCredential` bezit.
      * In Adobe Access Server for Protected Streaming moet de huidige referentie de eerste referentie zijn die is opgegeven in het element `LicenseServerCredential` in het bestand flashaccess-huurder.xml.
   * Zorg ervoor dat de huidige en oude gegevens worden doorgegeven aan `AsymmetricKeyRetrieval`

      * In de verwijzingsimplementatie, plaats het door `LicenseHandler.ServerCredential` en `AsymmetricKeyRetrieval.ServerCredential. n` eigenschappen.
      * In Adobe Access Server voor Beschermde Streaming, worden de oude geloofsbrieven gespecificeerd na de eerste referentie in het `LicenseServerCredential` element in het flashaccess-huurder.xml- dossier.

   Voor de vervoergeloofsbrieven:

   * Zorg ervoor dat de huidige referentie wordt doorgegeven aan de methode `HandlerConfiguration.setServerTransportCredential()`:

      * In de verwijzingsimplementatie, plaats het door het `HandlerConfiguration.ServerTransportCredential` bezit.
      * In Adobe Access Server voor beschermde het stromen, moet de huidige referentie de eerste referentie zijn die in het `TransportCredential` element in het flashaccess-huurder.xml- dossier wordt gespecificeerd.
   * Zorg ervoor dat de oude gegevens worden doorgegeven aan `HandlerConfiguration.setAdditionalServerTransportCredentials`():

      * In de verwijzingsimplementatie, plaats het door de `HandlerConfiguration.AdditionalServerTransportCredential. n` eigenschappen.
      * In Adobe Access Server voor beschermde het stromen, wordt dit gespecificeerd na de eerste referentie in het `TransportCredential` element in het flashaccess-huurder.xml- dossier.




1. Werk de verpakkingsgereedschappen bij om ervoor te zorgen dat ze inhoud verpakken met de huidige gegevens. Zorg ervoor dat het nieuwste certificaat van de licentieserver, het transportcertificaat en de referentie van de verpakker worden gebruikt voor het verpakken.
1. U kunt als volgt het licentieservercertificaat van de sleutelserver bijwerken:

   * Werk de geloofsbrieven in het de configuratiedossier van de Server van de Server van de Toegang van de Toegang van de Adobe. bij Omvat zowel de oude als de nieuwe Belangrijke geloofsbrieven van de Server in flashaccess-keyserver-huurder.xml.
   * Zorg ervoor dat het huidige certificaat wordt doorgegeven aan de methode `HandlerConfiguration.setKeyServerCertificate()`.

      * In de verwijzingsimplementatie, plaats het door het `HandlerConfiguration.KeyServerCertificate` bezit.
      * In Adobe Access Server voor Beschermde Streaming, specificeer het certificaat van de Server van de Sleutel in door het configuratie/Aannemer/Certificates/KeyServer element.

