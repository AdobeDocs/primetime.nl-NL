---
title: De BES-voorbeeldimplementatie opbouwen
description: De BES-voorbeeldimplementatie opbouwen
copied-description: true
exl-id: 330c14de-fe4e-4cc8-b0a5-8f7c74417adf
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# De BES-voorbeeldimplementatie opbouwen {#build-the-bees-reference-implementation}

Zorg ervoor dat u Java 1.6.0_24 of hoger gebruikt.
1. De benodigde lege paden vullen, zoals `tomcatdir` en `fasterxmldir` in [!DNL build-bees.xml]

   Snellere XML/Jackson is opgenomen. U kunt het ook downloaden van [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. Werkelijke jar-bestandsnamen bijwerken in [!DNL build.common.xml] als u een andere versie van de Jackson-bibliotheken wilt gebruiken.
1. Voer de `all` doel van [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

De [!DNL bees.war] wordt in het [!DNL bees-build/wars] map.
