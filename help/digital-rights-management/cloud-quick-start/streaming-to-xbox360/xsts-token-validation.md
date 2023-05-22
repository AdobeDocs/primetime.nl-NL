---
title: Xbox Live XSTS-tokenvalidatie
description: Xbox Live XSTS-tokenvalidatie
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Xbox Live XSTS-tokenvalidatie{#xbox-live-xsts-token-validation}

Voor XSTS-aanvragen `customerSpecificAuthToken` Het veld bevat het token Base64-codering voor XSTS. Het voorbeeld `XSTSValidator` de code onderzoekt Base64 gedecodeerde teken voor het bestaan van `EncryptedAssertion` element; echter, kunt u andere methodes gebruiken om tussen deze verzoeken en niet-Xbox verzoeken te onderscheiden. U kunt bijvoorbeeld een andere URL gebruiken.

Het beleid dat in het antwoordbericht wordt geretourneerd, overschrijft het oorspronkelijke beleid in de DRM-metagegevens die bij de Xbox key-aanvraag worden geleverd. Slechts wordt een ondergroep van beleidseigenschappen gesteund door de Xbox cliënt, en deze gebieden zijn de enige die het originele beleid zullen met voeten treden.

Er zijn extra opstellingsstappen nodig om symbolische decryptie en bevestiging te steunen. U moet de opdracht [!DNL xsts_partner_cert.pfx] en [!DNL x_secure_token_service.part.xboxlive.com.cer] referenties naar een sleutelarchief met JKS-indelingen, dat u vervolgens aan uw back-end machtigingsserver opgeeft als de eigenschap system `xsts-keystore`. Door gebrek, de partner [!DNL .pfx] heeft de alias `xsts`en het token validation cert heeft de alias `xsts-verify-cert`. U kunt deze ook overschrijven met behulp van systeemeigenschappen. Tot slot is er een systeembezit `xsts-keystore-password` die geen standaardwaarde heeft en die het sleutelarchiefwachtwoord bevat. De systeemeigenschappen die door de `XSTSValidator` de code wordt hieronder samengevat:

| Systeemeigenschap | Standaardwaarde | Opmerking |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | Het sleutelarchief met JKS-indelingen dat door de validator wordt gebruikt. |
| `xsts-keystore-password` |  | Wachtwoord voor het sleutelarchief |
| `xsts-alias` | `xsts` | Alias die wordt gebruikt om de decryptiesleutel van keystore terug te winnen |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | Alias die wordt gebruikt om het validatiecertificaat van keystore terug te winnen |

