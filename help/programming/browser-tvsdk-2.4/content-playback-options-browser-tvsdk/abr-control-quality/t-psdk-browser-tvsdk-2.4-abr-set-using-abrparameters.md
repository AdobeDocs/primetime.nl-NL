---
description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
title: Aangepaste bitsnelheden configureren met behulp van ABRControlParameters
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Aangepaste bitsnelheden configureren met behulp van ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.

Voor `ABRControlParameters`:

* U moet waarden opgeven voor alle parameters tijdens de constructietijd.
* U kunt afzonderlijke waarden niet wijzigen na de constructietijd.
* Als de parameters die u opgeeft, zich buiten het toegestane bereik bevinden, `ArgumentError` wordt gegenereerd.

1. Bepaal het beleid ABR:

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. De ABR-parameterwaarden instellen in het dialoogvenster `ABRControlParameters` en deze aan de Media Player toewijzen.

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```
