---
seo-title: De gebruiksmodeldemo inschakelen
title: De gebruiksmodeldemo inschakelen
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# De gebruiksmodeldemo inschakelen{#enable-the-usage-model-demo}

1. Geef de aangepaste eigenschap op `RI_UsageModelDemo=true` in de pakkettijd.

   Als u inhoud verpakt met de opdrachtregeltool van Media Packager, voert u het volgende in:

   ```
   java -jar AdobeMediaPackager.jar [
   
<i>source_file</i>] [dest_file<i></i>] -k RI_UsageModelDemo=true

```
>[!NOTE] {class="- topic/note "}
>
>If you do not activate the optional demo mode at packaging time, the license server issues a license based on the first valid DRM policy it processes.

