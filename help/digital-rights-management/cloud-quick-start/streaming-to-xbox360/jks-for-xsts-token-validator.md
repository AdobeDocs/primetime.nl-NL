---
title: JKS maken voor een XSTS-validator
description: JKS maken voor een XSTS-validator
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---


# JKS maken voor een XSTS-validator{#create-jks-for-an-xsts-validator}

1. Zoek de alias-naam van de persoonlijke cert op in het bestand [!DNL .pfx] van de partner.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. [!DNL .pfx] omzetten in [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (waarbij `<alias>` de alias van het privé cert is die u in Stap 1 ontdekte.)
1. Importeren [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Plaats [!DNL xsts.jks] in uw thuismap van Tomcat en definieer `-Dxsts-keystore-password=****` voor Tomcat.

Als [!DNL xsts_partner_cert.pfx] en [!DNL xsts.jks] verschillende wachtwoorden gebruiken, werk `xsts` wachtwoord in `jks` bij om hen het zelfde te maken.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
