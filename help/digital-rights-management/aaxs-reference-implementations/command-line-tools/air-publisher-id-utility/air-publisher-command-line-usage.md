---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
