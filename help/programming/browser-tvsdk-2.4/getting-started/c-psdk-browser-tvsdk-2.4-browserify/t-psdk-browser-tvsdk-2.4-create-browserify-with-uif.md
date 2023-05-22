---
description: Gebruik de Browser bibliotheekbestanden die door Browser TVSDK in uw app worden geleverd om een Browser-Compatibele speler tot stand te brengen gebruikend UI-Kader.
title: Creeer een Browser-Compatibele speler gebruikend UI-Kader
exl-id: cd72cae1-f67e-4192-9a7e-1c1492d88922
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Creeer een Browser-Compatibele speler gebruikend UI-Kader {#create-a-browserify-compatible-player-using-the-ui-framework}

Gebruik de Browser bibliotheekbestanden die door Browser TVSDK in uw app worden geleverd om een Browser-Compatibele speler tot stand te brengen gebruikend UI-Kader.

Voorbeeld van Browser-bestanden die zijn opgenomen in de TVSDK:

* [!DNL [...]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [...]/samples/browserify/ui-framework/build/package.json]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [...]/samples/browserify/ui-framework/examples/sample.js]

Als u een toepassing wilt maken die compatibel is met Browser, moet u `require` de twee Browser modules (verstrekt door Browser TVSDK) in uw toepassingscode:

1. Vereisen Browser modules:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Ga verder met ontwikkeling zoals beschreven in [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>U kunt nu een bundel maken van uw toepassingsbestanden met behulp van Bladeren.
