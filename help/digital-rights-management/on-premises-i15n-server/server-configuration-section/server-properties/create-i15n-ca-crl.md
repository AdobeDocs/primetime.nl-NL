---
title: Individuele CA CRL maken
description: Individuele CA CRL maken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Individuele CA CRL maken{#create-individualization-ca-crl}

Dit CRL-distributiepunt (Certificate Revocation List) maakt deel uit van elk machinecertificaat dat door de individualization-server wordt uitgegeven. Tijdens de validatie van machinecertificaten op de licentieserver wordt dit CRL gedownload van het distributiepunt dat in het certificaat wordt vermeld (of van de cache wordt gelezen als het al is gedownload) en gecontroleerd om er zeker van te zijn dat het certificaat niet is ingetrokken.

>[!NOTE]
>
>Als u de URL voor het CRL-distributiepunt wilt instellen, moet u het veld [!DNL AdobeInitial.properties] `cert.machine.crldp` instellen. Dit distributiepunt wordt *niet* gecontroleerd door Primetime DRM voor geldigheid. U moet controleren of deze URL geldig is. Fouten als gevolg van een ongeldige URL worden pas zichtbaar als validatiefouten worden weergegeven op de licentieserver.

Hieronder vindt u vereenvoudigde voorbeeldinstructies voor het gebruik van OpenSSL om CRL&#39;s te maken die uw licentieserver kan gebruiken. Adobe raadt u aan deze stappen op een veilige manier en in een veilige omgeving uit te voeren, zodra er een referentie voor de productiedeskundigheid is verkregen.

1. Wijzig de werkmap in de map [!DNL create_crl] die in deze distributie is opgenomen.
1. Kopieer uw Individualisatie CA [!DNL pfx] aan de zelfde [!DNL create_crl] folder.

   De verdere stappen veronderstellen dat de Individualisatie CA pfx [!DNL i15n.pfx] wordt genoemd. Pas de instellingen naar wens aan.
1. Pak de persoonlijke sleutel van het bestand Individualization CA [!DNL pfx] uit.

   ```
   openssl pkcs12 -ini15n.pfx -nocerts -out i15n_priv.pem
   ```

1. Zet de persoonlijke sleutel om in [!DNL pksc8] formaat.

   ```
   openssl pkcs8 -topk8 -in i15n_priv.pem -inform pem -out i15n_pk8.pem -outform pem -nocrypt
   ```

1. Genereer de CRL.

   ```
   openssl ca -keyform pem -keyfile ./i15n_pk8.pem -cert i15n.pem -gencrl  
     -out onprem-individualization -ca.crl
   ```

   In dit voorbeeld wordt een CRL gemaakt met een standaardgeldigheidsperiode van 1 maand. Gebruik de opties `-crldays` en `-crlhours` om de standaardwaarden met voeten te treden.

   Wanneer u een CRL genereert, worden [!DNL index] en [!DNL crlnumber] gebruikt, waarnaar in uw [!DNL openssl.conf] wordt verwezen. Standaard wordt de locatie [!DNL demoCA] in de werkmap gebruikt. Voorbeeldbestanden [!DNL index] en [!DNL crlnumber] worden opgenomen in de meegeleverde map [!DNL demoCA].

1. Implementeer het CRL-bestand dat in de vorige stap is gegenereerd naar een geschikte locatie die bereikbaar is door de licentieserver (bijvoorbeeld: individualisatieserver [!DNL ROOT]).
1. Start de licentieserver opnieuw zodra de CRL is geïnstalleerd.
