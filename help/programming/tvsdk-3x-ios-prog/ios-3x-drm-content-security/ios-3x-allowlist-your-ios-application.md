---
description: U kunt OS-toepassingen lijsten van gewenste personen met het gereedschap Adobe.
title: De iOS-toepassing lijsten van gewenste personen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---


# Uw iOS-toepassing {#allowlist-your-ios-application} lijsten van gewenste personen

U kunt OS-toepassingen lijsten van gewenste personen met het gereedschap Adobe.

Als u een TVSDK-toepassing hebt voltooid, kunt u doorgaans Adobe Primetime DRM-opdrachtregelprogramma&#39;s gebruiken voor het lijsten van gewenste personen van uw app.

>[!TIP]
>
>U kunt deze hulpmiddelen ook gebruiken om beleid te creëren DRM en inhoud te coderen.

Als u een aanbieding van uw app toestaat, weet u zeker dat beveiligde inhoud alleen in uw videospeler kan worden afgespeeld. Als u echter een iOS-toepassing wilt aanbieden, moet u de speciale procedure voltooien die werkt met het verzendbeleid van Apple voor toepassingen.

Voordat u een iOS-app verzendt, moet u deze ondertekenen en publiceren naar Apple.

>[!NOTE]
>
>Apple verwijdert de handtekening van uw ontwikkelaar en ondertekent de toepassing opnieuw met een eigen certificaat.

Vanwege de nieuwe ondertekening kunt u de aanbiedingsgegevens die u hebt gegenereerd voordat u deze naar de Apple App Store hebt verzonden, niet gebruiken.

Als u met dit verzendbeleid wilt werken, heeft Adobe een `machotools`-programma gemaakt waarmee uw iOS-toepassing een vingerafdruk maakt om een samenvattingswaarde te maken, deze waarde te ondertekenen en deze waarde in uw iOS-toepassing te injecteren. Nadat u de vingerafdruk van uw iOS-app hebt gemaakt, kunt u de app indienen bij de Apple App Store. Wanneer een gebruiker uw app uitvoert vanuit de App Store, voert Primetime DRM een runtimeberekening uit van de vingerafdruk van de toepassing en wordt deze bevestigd met de samenvattingswaarde die eerder in de toepassing is geïnjecteerd. Als de vingerafdruk overeenkomt, wordt bevestigd dat de app in de lijst staat en mag de beveiligde inhoud worden afgespeeld.

Het gereedschap Adobe `machotools` is opgenomen in de iOS TVSDK SDK, in de [!DNL [..]/tools/DRM]-map.

`machotools` gebruiken:

1. Een sleutelpaar genereren.

   Als u een hulpprogramma zoals OpenSSL wilt gebruiken, opent u een opdrachtvenster en voert u het volgende in:

   ```shell
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. Voer desgevraagd een wachtwoord in om de persoonlijke sleutel te beveiligen.

   Wachtwoorden moeten ten minste 12 tekens bevatten en de tekens moeten bestaan uit een combinatie van ASCII-tekens en getallen in hoofdletters en kleine letters.
1. Als u OpenSSL wilt gebruiken om een sterk wachtwoord voor u te genereren, opent u een opdrachtvenster en voert u het volgende in:

   ```shell
   openssl rand -base64 8
   ```

1. Genereer een CSR (Certificate Signing Request).

   Als u OpenSSL wilt gebruiken om een CSR te genereren, opent u een opdrachtvenster en voert u het volgende in:

   ```shell
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. Onderteken het certificaat zelf en voer een willekeurige duur in.

   In het volgende voorbeeld wordt een vervaldatum van 20 jaar gegeven:

   ```shell
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. Converteer het zelfondertekende certificaat naar een PKCS#12-bestand:

   ```shell
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   U kunt het zelfondertekende certificaat gebruiken om uw iOS-app te ondertekenen.

1. Werk de locatie van het PFX-bestand en wachtwoord bij.
1. Voordat u uw toepassing gaat ontwikkelen in Xcode, gaat u naar **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** en voegt u de volgende opdracht toe aan uw runscript:

   ```shell
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. Voer [!DNL machotools] uit om de hashwaarde van uw app Publisher-id te genereren.

   ```shell
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. Creeer een nieuw Beleid DRM of werk uw bestaand beleid bij om de teruggekeerde waarde van het knoeiboel van identiteitskaart van de Uitgever te omvatten.
1. Creëer met behulp van [!DNL AdobePolicyManager.jar] een nieuw DRM-beleid (werk uw bestaande beleid bij) om de geretourneerde hashwaarde van uitgever-id, een optionele toepassings-id en min- en max-versiekenmerken op te nemen in het opgenomen [!DNL flashaccess-tools.properties]-bestand.

   ```shell
   java -jar libs/AdobePolicyManager.jar new app_allowlist.pol
   ```

1. Verpak de inhoud met het nieuwe DRM-beleid en bevestig het afspelen van de inhoud van de lijst met toegestane inhoud in uw iOS-app.
