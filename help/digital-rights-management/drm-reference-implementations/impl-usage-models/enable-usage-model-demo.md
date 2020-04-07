---
seo-title: De gebruiksmodeldemo inschakelen
title: De gebruiksmodeldemo inschakelen
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 6e949c2f88deef88f0d0ac95b18c006da1c89d2f

---


# De gebruiksmodeldemo inschakelen{#enable-the-usage-model-demo}

1. Geef de aangepaste eigenschap op `RI_UsageModelDemo=true` in de pakkettijd.

   Als u inhoud verpakt met de opdrachtregeltool van Media Packager, voert u het volgende in:

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Als u de optionele demo-modus niet activeert tijdens het verpakken, geeft de licentieserver een licentie op basis van het eerste geldige DRM-beleid dat door de server wordt verwerkt.

