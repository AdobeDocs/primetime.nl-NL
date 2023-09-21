---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# Problemen oplossen {#troubleshooting}

Hieronder ziet u algemene problemen en oplossingen voor implementatie:

* Als u de volgende fout ziet:

  ```
      "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  Controleer of het wachtwoord is versleuteld met de beschikbare code `ScrambleUtil` klasse.

* Als u de volgende fout ziet:

  ```
      "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  Controleer of u het juiste gecodeerde wachtwoord voor het PFX-bestand hebt opgegeven.

* Als u de volgende fout ziet:

  ```
      "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  Zorg ervoor dat u de wachtwoordscrambler-klasse hebt gebruikt die bij de Reference Implementation wordt geleverd (dit hulpprogramma is anders dan het hulpprogramma dat bij de Adobe® Access™-server voor beveiligde streaming wordt geleverd).
