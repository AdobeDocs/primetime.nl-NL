---
description: 'null'
seo-description: 'null'
seo-title: Wachtwoorden voorbereiden met Ant
title: Wachtwoorden voorbereiden met Ant
uuid: 9419ab0d-b448-4881-9d26-35c00f0b13bc
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '42'
ht-degree: 4%

---


# Wachtwoorden voorbereiden met Ant{#prepare-passwords-using-ant}

Gebruik Ant om uw wachtwoord te coderen:

1. Ga naar `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Stel de eigenschap `sdkdir` in [!DNL build-refimpl.xml] in om te verwijzen naar de map die de Primetime DRM Java SDK bevat.
1. Voer de volgende opdracht uit:

   ```
   ant -f build-refimpl.xml
   ```

