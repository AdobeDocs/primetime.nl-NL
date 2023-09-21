---
title: De gebruiksmodeldemo inschakelen
description: De gebruiksmodeldemo inschakelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
