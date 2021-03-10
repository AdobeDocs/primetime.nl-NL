---
title: Wachtwoorden voorbereiden met Ant
description: Wachtwoorden voorbereiden met Ant
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 5%

---


# Wachtwoorden voorbereiden met Ant{#prepare-passwords-using-ant}

Gebruik Ant om uw wachtwoord te coderen:

1. Ga naar `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Stel de eigenschap `sdkdir` in [!DNL build-refimpl.xml] in om te verwijzen naar de map die de Primetime DRM Java SDK bevat.
1. Voer de volgende opdracht uit:

   ```
   ant -f build-refimpl.xml
   ```

