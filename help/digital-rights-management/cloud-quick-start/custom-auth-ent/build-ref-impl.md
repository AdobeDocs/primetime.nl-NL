---
seo-title: De BES-voorbeeldimplementatie opbouwen
title: De BES-voorbeeldimplementatie opbouwen
uuid: c9358188-e626-4f99-a02c-4928b06d6ae2
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# De BES-voorbeeldimplementatie {#build-the-bees-reference-implementation} samenstellen

Zorg ervoor dat u Java 1.6.0_24 of hoger gebruikt.
1. Vul de benodigde lege paden in, zoals `tomcatdir` en `fasterxmldir` in [!DNL build-bees.xml]

   Snellere XML/Jackson is opgenomen. U kunt het van [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core) ook downloaden.
1. Werk feitelijke jar bestandsnamen bij in [!DNL build.common.xml] als u een andere versie van de Jackson-bibliotheken wilt gebruiken.
1. Voer het `all`-doel van [!DNL build-bees.xml] uit:

   ```
   ant -f build-bees.xml
   ```

De [!DNL bees.war] wordt gemaakt in de map [!DNL bees-build/wars].