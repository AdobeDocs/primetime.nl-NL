---
seo-title: Individuele CA CRL maken
title: Individuele CA CRL maken
uuid: f722f3d1-517f-43e3-b892-f9287527fbe6
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Individuele CA CRL maken{#create-individualization-ca-crl}

Dit CRL-distributiepunt (Certificate Revocation List) maakt deel uit van elk machinecertificaat dat door de individualization-server wordt uitgegeven. Tijdens de validatie van machinecertificaten op de licentieserver wordt dit CRL gedownload van het distributiepunt dat in het certificaat wordt vermeld (of van de cache wordt gelezen als het al is gedownload) en gecontroleerd om er zeker van te zijn dat het certificaat niet is ingetrokken.

>[!NOTE]
>
>Als u de URL voor het CRL-distributiepunt wilt instellen, moet u het [!DNL AdobeInitial.properties] `cert.machine.crldp` veld instellen. Dit distributiepunt wordt *niet* door Primetime DRM gecontroleerd op geldigheid. U moet controleren of deze URL geldig is. Fouten als gevolg van een ongeldige URL worden pas zichtbaar als validatiefouten worden weergegeven op de licentieserver.

Hieronder vindt u vereenvoudigde voorbeeldinstructies voor het gebruik van OpenSSL om CRL&#39;s te maken die uw licentieserver kan gebruiken. Adobe raadt u aan deze stappen op een veilige manier en in een veilige omgeving uit te voeren, zodra een referentie voor de productie van individuele gebruikers is verkregen.

1. Wijzig de werkmap in de [!DNL create_crl] map die in deze distributie is opgenomen.
1. Kopieer uw Individualisatie CA [!DNL pfx] aan de zelfde [!DNL create_crl] folder.

   De verdere stappen veronderstellen dat pfx van Individualization CA wordt genoemd [!DNL i15n.pfx]. Pas de instellingen naar wens aan.
1. Pak de persoonlijke sleutel van het CA- [!DNL pfx] bestand voor individualisatie uit.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Zet de persoonlijke sleutel om in de [!DNL pksc8] indeling.

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Genereer de CRL.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   In dit voorbeeld wordt een CRL gemaakt met een standaardgeldigheidsperiode van 1 maand. Gebruik de opties `-crldays` en `-crlhours` opties om de standaardwaarden te overschrijven.

   Bij het genereren van een CRL worden de gegevens [!DNL index] en het [!DNL crlnumber] bestand gebruikt waarnaar in uw [!DNL openssl.conf]. Standaard wordt de [!DNL demoCA] locatie in de werkmap gebruikt. Voorbeeldbestanden [!DNL index] en [!DNL crlnumber] bestanden worden opgenomen in de opgegeven [!DNL demoCA] directory.

1. Implementeer het CRL-bestand dat in de vorige stap is gegenereerd naar een geschikte locatie die bereikbaar is door de licentieserver (bijvoorbeeld: individualisatieserver [!DNL ROOT]).
1. Start de licentieserver opnieuw zodra de CRL is geïnstalleerd.
