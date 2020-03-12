---
seo-title: JKS maken voor een XSTS-validator
title: JKS maken voor een XSTS-validator
uuid: e02b517d-0b72-4e95-92b2-09b8f785cce6
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# JKS maken voor een XSTS-validator{#create-jks-for-an-xsts-validator}

1. Zoek de alias-naam van de persoonlijke cert op in het [!DNL .pfx] partnerbestand.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Omzetten [!DNL .pfx] in [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (waarbij `<alias>` de alias van het privé certificaat de naam is die u in Stap 1 ontdekte.)
1. Importeren [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Plaats [!DNL xsts.jks] in uw Tomcat huisfolder, en bepaal `-Dxsts-keystore-password=****` voor Tomcat.

Als [!DNL xsts_partner_cert.pfx] en [!DNL xsts.jks] gebruiken verschillende wachtwoorden, werk het `xsts` wachtwoord in bij `jks` om hen het zelfde te maken.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
