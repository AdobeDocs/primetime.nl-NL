---
title: Overzicht
description: Overzicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# AIR Publisher ID-hulpprogramma {#air-publisher-id-utility}

Wanneer u een AIR-bestand maakt, genereert ADT (AIR Developer Tool) automatisch een uitgevers-id. Het hulpprogramma AIR Publisher ID ( [!DNL AdobePublisherIDUtility.jar]) berekent de uitgever-id voor een AIR-toepassing.

De uitgevers-id is uniek voor het certificaat dat u gebruikt om een AIR-bestand te maken. Als u hetzelfde certificaat opnieuw gebruikt voor meerdere AIR-toepassingen, hebben alle AIR-toepassingen dezelfde uitgevers-id. Een AIR-versie die in versie 1.5.2 slaagt, voegt de gegenereerde uitgevers-id niet toe aan een bestand. Daarom als u van plan bent om een lijst van gewenste personen van de toepassing van AIR te gebruiken, gebruik dit hulpmiddel om Uitgever te bepalen identiteitskaart

>[!NOTE]
>
>De uitgevers-id die wordt gebruikt voor de handhaving van de AIR-lijst van gewenste personen, is niet dezelfde als de uitgever van de toepassing die in de toepassing is opgegeven [!DNL application.xml] bestand.

## Opdrachtregelgebruik van het AIR Publisher ID-hulpprogramma {#air-publisher-id-utility-command-line-usage}

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

* `signaturefile` geeft een pad op naar de [!DNL signatures.xml] bestand, in de toepassingen [!DNL META-INF] directory

* `signingcert` geeft het certificaat aan dat wordt gebruikt voor de ondertekening van een AIR-toepassing

>[!NOTE]
>
>Als u de uitgevers-id voor een Android-toepassing wilt bepalen, moet u de opdracht `-s` op om het certificaat op te geven waarmee het APK (Android application package) wordt ondertekend. Primetime DRM is vereist om Android-toepassingen te maken die met Primetime DRM beveiligde inhoud kunnen afspelen.
