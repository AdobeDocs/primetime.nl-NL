---
description: Gebruik de Browser bibliotheekbestanden die door Browser TVSDK in uw app worden geleverd om een Browser-Compatibele speler tot stand te brengen gebruikend UI-Kader.
seo-description: Gebruik de Browser bibliotheekbestanden die door Browser TVSDK in uw app worden geleverd om een Browser-Compatibele speler tot stand te brengen gebruikend UI-Kader.
seo-title: Creeer een Browser-Compatibele speler gebruikend UI-Kader
title: Creeer een Browser-Compatibele speler gebruikend UI-Kader
uuid: 544fd872-5ca1-417d-8aab-69613caada0e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Creeer een Browser-Compatibele speler gebruikend UI-Kader {#create-a-browserify-compatible-player-using-the-ui-framework}

Gebruik de Browser bibliotheekbestanden die door Browser TVSDK in uw app worden geleverd om een Browser-Compatibele speler tot stand te brengen gebruikend UI-Kader.

Voorbeeld van Browser-bestanden die zijn opgenomen in de TVSDK:

* [!DNL [..]/samples/browserify/ui-framework/build/Gruntfile.js]
* [!DNL [..]/samples/browserify/ui-framework/build/package.json]
* [!DNL [..]/samples/browserify/ui-framework/examples/sample.html]
* [!DNL [..]/samples/browserify/ui-framework/examples/sample.js]

Als u een toepassing wilt maken die compatibel is met Browserbesturing en die gebruikmaakt van het UI-framework, moet u `require` de twee Browser-TVSDK-modules (geleverd door Browser-TVSDK) in uw toepassingscode opgeven:

1. Vereisen Browser modules:

   ```
   var AdobePSDK = require('../../../../frameworks/player/AdobePSDK.module.js');  
   var ptp = require('../../../ui-framework/libs/Primetimevisualapi.module.js);  
   […]
   ```

1. Ga verder met ontwikkeling zoals beschreven in [](../../../browser-tvsdk-2.4/getting-started/c-psdk-browser-tvsdk-2.4-create-a-basic-player/t-psdk-browser-tvsdk-2.4-create-basic-player-uif.md).
>U kunt nu een bundel maken van uw toepassingsbestanden met behulp van Bladeren.
