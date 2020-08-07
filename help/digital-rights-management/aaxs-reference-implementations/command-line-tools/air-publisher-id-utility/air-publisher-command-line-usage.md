---
seo-title: Gebruik van opdrachtregels
title: Gebruik van opdrachtregels
uuid: 54b1e867-c6cc-4355-b8e6-a7ec910bd33d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
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

* 
   * `signaturefile`* geeft het pad aan naar het bestand signatures.xml van de AIR-toepassing in de [!DNL META-INF] map met toepassingen.

* `signingcert` geeft het certificaat aan waarmee de AIR-toepassing wordt ondertekend

>[!NOTE]
>
>Als u de uitgevers-id voor een iOS-toepassing wilt bepalen, gebruikt u de `-s` optie en geeft u het certificaat op waarmee de iOS-toepassing wordt ondertekend. ***Adobe Primetime is vereist voor het maken van iOS-toepassingen die met Access beveiligde inhoud*** kunnen afspelen.

