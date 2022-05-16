---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
exl-id: 67056085-beb5-4f54-8962-369bc32d7907
source-git-commit: 79cab347d0daa01549fbf8a9b37bf0a91c14648e
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# Gebruik van opdrachtregels {#command-line-usage}

Gebruik de volgende syntaxis om het gereedschap uit te voeren:

```
java -jar AdobePublisherIDUtility.jar 
<i class="+ topic ph hi-d="" i "="">
 <i class="+ topic ph hi-d="" i "="">
  signaturefile 
  java -jar AdobePublisherIDUtility.jar -s 
  <i class="+ topic ph hi-d="" i "="">
    signingcert
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* `signaturefile` geeft het pad aan naar het bestand signatures.xml van de AIR-toepassing in de toepassingen [!DNL META-INF] directory

* `signingcert` geeft het certificaat aan waarmee de AIR-toepassing wordt ondertekend

>[!NOTE]
>
>Als u de uitgevers-id voor een iOS-toepassing wilt bepalen, gebruikt u de `-s` en geeft u het certificaat op waarmee de iOS-toepassing wordt ondertekend. ***Adobe Primetime is vereist om iOS-toepassingen te maken die met Access beveiligde inhoud kunnen afspelen***.
