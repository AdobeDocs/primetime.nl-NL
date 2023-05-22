---
title: De gebruiksmodeldemo inschakelen
description: De gebruiksmodeldemo inschakelen
copied-description: true
exl-id: 5d546f1a-ebf6-4c93-9a73-fa812cd71086
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# De gebruiksmodeldemo inschakelen{#enable-the-usage-model-demo}

1. De aangepaste eigenschap opgeven `RI_UsageModelDemo=true` op het tijdstip van verpakking.

   Als u inhoud verpakt met de opdrachtregeltool van Media Packager, voert u het volgende in:

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Als u de optionele demo-modus niet activeert tijdens het verpakken, geeft de licentieserver een licentie op basis van het eerste geldige DRM-beleid dat door de server wordt verwerkt.
