---
title: JKS maken voor een XSTS-validator
description: JKS maken voor een XSTS-validator
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---


# JKS maken voor een XSTS-validator{#create-jks-for-an-xsts-validator}

1. Zoek de alias-naam van de persoonlijke cert op die zich in de partner bevindt [!DNL .pfx] bestand.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Omzetten [!DNL .pfx] tot [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   waarbij `<alias>` is de alias van de privé cert naam die u in Stap 1 ontdekte.)
1. Importeren [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Put [!DNL xsts.jks] in uw Tomcat-thuismap en definieer `-Dxsts-keystore-password=****` voor Tomcat.

Indien [!DNL xsts_partner_cert.pfx] en [!DNL xsts.jks] gebruikt verschillende wachtwoorden, werkt u de `xsts` wachtwoord in `jks` om ze gelijk te maken.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
