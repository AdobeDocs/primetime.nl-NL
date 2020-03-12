---
seo-title: Bestanden converteren
title: Bestanden converteren
uuid: e17ee003-5ac2-4bb8-83b7-81ee8fa9ee46
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Bestanden converteren{#convert-files}

Met behulp van een hulpprogramma zoals OpenSSL en de persoonlijke sleutel genereert de aanvrager de bestanden PKCS#12 (pfx) en PEM/DER door de volgende opdrachten in te voeren in een opdrachtvenster:

1. PKCS#7-bestand converteren naar een tijdelijk PEM-bestand.

   Als u OpenSSL wilt gebruiken, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >Dit tijdelijke PEM bevat uw certificaat en de certificaten voor tussenliggende CA&#39;s. Gebruik deze certificaten om het PFX-bestand te genereren.

1. Zet het tijdelijke PEM-bestand om in een PFX-bestand.

   Als u OpenSSL wilt gebruiken, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl pkcs12 -export -inkey mycompany-license.key -in mycompany-license-temp.pem \ 
   -out mycompany-license.pfx -passin pass:private_key_password -passout pass:pfx_password 
   ```

1. Zet het tijdelijke PEM-bestand om in een definitief PEM-bestand.

   Als u OpenSSL wilt gebruiken, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl x509 -in mycompany-license-temp.pem -inform PEM -out mycompany-license.pem -outform PEM 
   ```

   >[!NOTE]
   >
   >Hoewel niet vereist, raadt Adobe u aan verschillende wachtwoorden te gebruiken voor de persoonlijke sleutel (private_key_password) en de PFX (pfx_password).

   Dit definitieve PEM-bestand bevat alleen uw certificaat.

1. Zet het PEM-bestand om in een DER-bestand.

   Als u OpenSSL wilt gebruiken, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >DER-bestanden zijn alleen vereist voor het HTTP Dynamic Streaming-pakket.

