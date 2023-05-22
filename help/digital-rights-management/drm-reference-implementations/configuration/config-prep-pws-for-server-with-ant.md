---
title: Wachtwoorden voorbereiden met Ant
description: Wachtwoorden voorbereiden met Ant
copied-description: true
exl-id: 78f00fd7-ca9c-49a9-9e4b-6d1e2daf9241
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
