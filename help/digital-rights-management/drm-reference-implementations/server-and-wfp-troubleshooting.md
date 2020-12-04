---
description: 'null'
seo-description: 'null'
seo-title: Problemen oplossen
title: Problemen oplossen
uuid: 06b86067-1ff6-4b4e-922f-7f968260ba19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Problemen oplossen{#troubleshooting}

Hier volgen enkele problemen en oplossingen die u tijdens de implementatie kunt tegenkomen.

* Als het volgende foutbericht wordt weergegeven:

   ```
   "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   Controleer of het wachtwoord is gecodeerd met de klasse `ScrambleUtil`.

* Als het volgende foutbericht wordt weergegeven:

   ```
   "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Controleer of u het juiste gecodeerde wachtwoord hebt opgegeven in het PFX-bestand.

* Als het volgende foutbericht wordt weergegeven:

   ```
   "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Zorg ervoor dat u de wachtwoordscrambler-klasse *gebruikt die bij de implementatie van de Verwijzing is geleverd*. Dit hulpprogramma is anders dan het hulpprogramma dat is meegeleverd bij de Adobe Primetime DRM-server voor beveiligde streaming.

