---
title: Wachtwoorden voorbereiden met Ant
description: Wachtwoorden voorbereiden met Ant
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Wachtwoorden voorbereiden met Ant{#prepare-passwords-using-ant}

Gebruik Ant om uw wachtwoord te coderen:

1. Navigeren naar `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. Stel de `sdkdir` eigenschap in [!DNL build-refimpl.xml] om naar de map te verwijzen die de Primetime DRM Java SDK bevat.
1. Voer de volgende opdracht uit:

   ```
   ant -f build-refimpl.xml
   ```
