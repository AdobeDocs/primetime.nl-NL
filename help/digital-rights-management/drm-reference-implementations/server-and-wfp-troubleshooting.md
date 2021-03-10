---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
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

   Zorg ervoor dat u de wachtwoordscrambler-klasse *gebruikt die is meegeleverd bij Referentie-implementatie*. Dit hulpprogramma is anders dan het hulpprogramma dat is meegeleverd bij de Adobe Primetime DRM-server voor beveiligde streaming.

