---
title: Xbox Live XSTS-tokenvalidatie
description: Xbox Live XSTS-tokenvalidatie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Xbox Live XSTS-tokenvalidatie{#xbox-live-xsts-token-validation}

Voor XSTS-aanvragen bevat het veld `customerSpecificAuthToken` het token Base64 met codering XSTS. De voorbeeldcode `XSTSValidator` onderzoekt het gedecodeerde Base64 teken voor het bestaan van het `EncryptedAssertion` element; echter, kunt u andere methodes gebruiken om tussen deze verzoeken en niet-Xbox verzoeken te onderscheiden. U kunt bijvoorbeeld een andere URL gebruiken.

Het beleid dat in het antwoordbericht wordt geretourneerd, overschrijft het oorspronkelijke beleid in de DRM-metagegevens die bij de Xbox key-aanvraag worden geleverd. Slechts wordt een ondergroep van beleidseigenschappen gesteund door de Xbox cliënt, en deze gebieden zijn de enige die het originele beleid zullen met voeten treden.

Er zijn extra opstellingsstappen nodig om symbolische decryptie en bevestiging te steunen. U moet de [!DNL xsts_partner_cert.pfx] en [!DNL x_secure_token_service.part.xboxlive.com.cer] geloofsbrieven in een JKS formaat keystore laden, die u dan aan uw achterste deelmachtigingsserver als systeembezit `xsts-keystore` verstrekt. Standaard heeft de partner [!DNL .pfx] de alias `xsts` en de tokenvalidatiecurt heeft de alias `xsts-verify-cert`. U kunt deze ook overschrijven met behulp van systeemeigenschappen. Tot slot is er een systeembezit `xsts-keystore-password` dat geen gebrek heeft, en dat het keystore wachtwoord bevat. De systeemeigenschappen die door de code `XSTSValidator` worden gelezen, worden hieronder samengevat:

| Systeemeigenschap | Standaardwaarde | Opmerking |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | Het sleutelarchief met JKS-indelingen dat door de validator wordt gebruikt. |
| `xsts-keystore-password` |  | Wachtwoord voor het sleutelarchief |
| `xsts-alias` | `xsts` | Alias die wordt gebruikt om de decryptiesleutel van keystore terug te winnen |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | Alias die wordt gebruikt om het validatiecertificaat van keystore terug te winnen |

