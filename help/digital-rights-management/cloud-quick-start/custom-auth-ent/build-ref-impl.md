---
seo-title: De BES-voorbeeldimplementatie opbouwen
title: De BES-voorbeeldimplementatie opbouwen
uuid: c9358188-e626-4f99-a02c-4928b06d6ae2
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# De BES-voorbeeldimplementatie opbouwen {#build-the-bees-reference-implementation}

Zorg ervoor dat u Java 1.6.0_24 of hoger gebruikt.
1. De benodigde lege paden zoals `tomcatdir` en `fasterxmldir` in vullen [!DNL build-bees.xml]

   Snellere XML/Jackson is opgenomen. U kunt het ook downloaden van [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. Werk eigenlijke jar bestandsnamen bij in [!DNL build.common.xml] als u een andere versie van de Jackson-bibliotheken wilt gebruiken.
1. Voer het `all` doel uit van [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

Het [!DNL bees.war] wordt gemaakt in de [!DNL bees-build/wars] map.