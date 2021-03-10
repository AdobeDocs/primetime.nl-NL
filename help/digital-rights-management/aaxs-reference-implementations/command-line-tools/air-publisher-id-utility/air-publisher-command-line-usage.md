---
title: Gebruik van opdrachtregels
description: Gebruik van opdrachtregels
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# Gebruik van opdrachtregel {#command-line-usage}

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

* 
   * `signaturefile`* geeft het pad aan naar het bestand signatures.xml van de AIR-toepassing in de  [!DNL META-INF] map met toepassingen.

* `signingcert` geeft het certificaat aan waarmee de AIR-toepassing wordt ondertekend

>[!NOTE]
>
>Als u de uitgevers-id voor een iOS-toepassing wilt bepalen, gebruikt u de optie `-s` en geeft u het certificaat op waarmee de iOS-toepassing wordt ondertekend. ***Adobe Primetime is vereist voor het maken van iOS-toepassingen waarmee met Access beveiligde inhoud*** kan worden afgespeeld.

