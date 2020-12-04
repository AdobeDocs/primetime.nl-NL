---
seo-title: Problemen oplossen
title: Problemen oplossen
uuid: db76d6a4-c285-4d86-95a1-4f1a85ed3743
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

   Controleer of het wachtwoord is versleuteld met de opgegeven `ScrambleUtil`-klasse.

* Als u de volgende fout ziet:

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   Controleer of u het juiste gecodeerde wachtwoord voor het PFX-bestand hebt opgegeven.

* Als u de volgende fout ziet:

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   Zorg ervoor dat u de wachtwoordscrambler-klasse gebruikt die bij de Reference Implementation wordt geleverd (dit hulpprogramma is anders dan het hulpprogramma dat bij de Adobe® Access™-server voor beveiligde streaming wordt geleverd).

