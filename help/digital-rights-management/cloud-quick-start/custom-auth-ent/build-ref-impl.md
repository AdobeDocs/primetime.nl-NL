---
title: De BES-referentieimplementatie opbouwen
description: De BES-referentieimplementatie opbouwen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# De BES-referentieimplementatie opbouwen {#build-the-bees-reference-implementation}

Zorg ervoor dat u Java 1.6.0_24 of hoger gebruikt.
1. De benodigde lege paden vullen, zoals `tomcatdir` en `fasterxmldir` in [!DNL build-bees.xml]

   Snellere XML/Jackson is opgenomen. U kunt het ook downloaden van [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. Werkelijke jar-bestandsnamen bijwerken in [!DNL build.common.xml] als u een andere versie van de Jackson-bibliotheken wilt gebruiken.
1. Voer de `all` doel van [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

De [!DNL bees.war] wordt in het [!DNL bees-build/wars] map.
