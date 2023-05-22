---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
exl-id: 4af7b625-63d3-48b6-98a5-b8894dd0c67f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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

   Zorg ervoor dat u de wachtwoordscrambler-klasse gebruikt die bij de Reference Implementation wordt geleverd (dit hulpprogramma is anders dan het hulpprogramma dat bij de Adobe® Access™-server voor beveiligde streaming wordt geleverd).
