---
title: Individuele CA CRL maken
description: Individuele CA CRL maken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Individuele CA CRL maken{#create-individualization-ca-crl}

Dit CRL-distributiepunt (Certificate Revocation List) maakt deel uit van elk machinecertificaat dat door de individualization-server wordt uitgegeven. Tijdens de validatie van machinecertificaten op de licentieserver wordt dit CRL gedownload van het distributiepunt dat in het certificaat wordt vermeld (of van de cache wordt gelezen als het al is gedownload) en gecontroleerd om er zeker van te zijn dat het certificaat niet is ingetrokken.

>[!NOTE]
>
>Om URL voor het CRL distributiepunt te plaatsen, zult u moeten plaatsen [!DNL AdobeInitial.properties] `cert.machine.crldp` veld. Dit distributiepunt is *niet* gecontroleerd door Primetime DRM voor geldigheid. U moet controleren of deze URL geldig is. Fouten als gevolg van een ongeldige URL worden pas zichtbaar als validatiefouten worden weergegeven op de licentieserver.

Hieronder vindt u vereenvoudigde voorbeeldinstructies voor het gebruik van OpenSSL om CRL&#39;s te maken die uw licentieserver kan gebruiken. De Adobe beveelt aan dat u deze stappen op een veilige manier en in een veilige omgeving uitvoert, zodra een referentie van de CA van de Individualisatie van de Productie is verkregen.

1. Wijzig de werkmap in de [!DNL create_crl] in deze distributie.
1. Kopieer uw CA voor individualisatie [!DNL pfx] aan dezelfde [!DNL create_crl] directory.

   De volgende stappen veronderstellen dat pfx van Individualisatie CA wordt genoemd [!DNL i15n.pfx]. Pas de instellingen naar wens aan.
1. Extraheer de Individuele CA [!DNL pfx] persoonlijke sleutel van het bestand.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. De persoonlijke sleutel omzetten in [!DNL pksc8] gebruiken.

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Genereer de CRL.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   In dit voorbeeld wordt een CRL gemaakt met een standaardgeldigheidsperiode van 1 maand. Gebruik de `-crldays` en `-crlhours` opties om de standaardwaarden te overschrijven.

   Als u een CRL genereert, wordt het [!DNL index] en [!DNL crlnumber] bestand waarnaar in uw [!DNL openssl.conf]. Standaard worden de [!DNL demoCA] de locatie in de werkmap wordt gebruikt. Monster [!DNL index] en [!DNL crlnumber] bestanden worden opgenomen in de opgegeven [!DNL demoCA] directory.

1. Implementeer het CRL-bestand dat in de vorige stap is gegenereerd naar een geschikte locatie die bereikbaar is door de licentieserver (bijvoorbeeld: individualisatieserver) [!DNL ROOT]).
1. Start de licentieserver opnieuw zodra de CRL is geïnstalleerd.
