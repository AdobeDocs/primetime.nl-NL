---
seo-title: Overzicht
title: Overzicht
uuid: f45c6b58-53c5-41e0-be3d-590231dd214a
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# AIR Publisher ID-hulpprogramma {#air-publisher-id-utility}

Wanneer u een AIR-bestand maakt, genereert ADT (AIR Developer Tool) automatisch een uitgevers-id. Het hulpprogramma AIR Publisher-id ( [!DNL AdobePublisherIDUtility.jar]) berekent de uitgevers-id voor een AIR-toepassing.

De uitgevers-id is uniek voor het certificaat dat u gebruikt om een AIR-bestand te maken. Als u hetzelfde certificaat opnieuw gebruikt voor meerdere AIR-toepassingen, hebben alle AIR-toepassingen dezelfde uitgevers-id. Een AIR-versie die in versie 1.5.2 slaagt, voegt de gegenereerde uitgevers-id niet toe aan een bestand. Als u daarom een lijst met toegestane AIR-toepassingen wilt gebruiken, gebruikt u dit gereedschap om de uitgevers-id te bepalen.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>De uitgevers-id die wordt gebruikt voor AIR staat handhaving van lijsten toe, is niet dezelfde als de uitgever van de toepassing die in het [!DNL application.xml] bestand van de toepassing opgeeft.

## Opdrachtregelgebruik van het hulpprogramma AIR Publisher ID {#air-publisher-id-utility-command-line-usage}

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
   * `signaturefile`* geeft een pad op naar het [!DNL signatures.xml] bestand van de AIR-toepassing in de [!DNL META-INF] map met toepassingen.

* `signingcert` geeft het certificaat aan dat wordt gebruikt om een AIR-toepassing te ondertekenen

>[!NOTE]
>
>Als u de uitgevers-id voor een Android-toepassing wilt bepalen, moet u de `-s` optie gebruiken om het certificaat op te geven waarmee het APK (Android application package) wordt ondertekend. Primetime DRM is vereist om Android-toepassingen te maken die met Primetime DRM beveiligde inhoud kunnen afspelen.