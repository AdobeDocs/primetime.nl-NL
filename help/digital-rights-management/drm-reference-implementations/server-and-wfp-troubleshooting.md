---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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

  Zorg ervoor dat het wachtwoord is gecodeerd met de `ScrambleUtil` klasse.

* Als het volgende foutbericht wordt weergegeven:

  ```
  "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  Controleer of u het juiste gecodeerde wachtwoord hebt opgegeven in het PFX-bestand.

* Als het volgende foutbericht wordt weergegeven:

  ```
  "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  Zorg ervoor dat u de wachtwoordklasse gebruikt *die bij de referentieuitvoering is geleverd*. Dit hulpprogramma is anders dan het hulpprogramma dat is meegeleverd bij de Adobe Primetime DRM-server voor beveiligde streaming.
