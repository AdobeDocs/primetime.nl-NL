---
description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
seo-description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
seo-title: Aangepaste bitsnelheden configureren met ABRControlParameters
title: Aangepaste bitsnelheden configureren met ABRControlParameters
uuid: 99b7a463-327b-48bf-8244-e41467072b44
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Aangepaste bitsnelheden configureren met ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.

Voor `ABRControlParameters` gelden de volgende voorwaarden:

* U moet waarden opgeven voor alle parameters tijdens de constructietijd.
* U kunt afzonderlijke waarden niet wijzigen na de constructietijd.
* Als de parameters die u opgeeft buiten het toegestane bereik vallen, wordt een `ArgumentError` gegenereerd.

1. Bepaal het beleid ABR:

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. Stel de ABR-parameterwaarden in de constructor `ABRControlParameters` in en wijs deze toe aan Mediaspeler.

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```

