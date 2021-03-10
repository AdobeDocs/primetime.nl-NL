---
title: De gebruiksmodeldemo inschakelen
description: De gebruiksmodeldemo inschakelen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# De demo van het gebruiksmodel inschakelen{#enable-the-usage-model-demo}

1. Geef de aangepaste eigenschap `RI_UsageModelDemo=true` op bij het verpakken.

   Als u inhoud verpakt met de opdrachtregeltool van Media Packager, voert u het volgende in:

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Als u de optionele demo-modus niet activeert tijdens het verpakken, geeft de licentieserver een licentie op basis van het eerste geldige DRM-beleid dat door de server wordt verwerkt.

