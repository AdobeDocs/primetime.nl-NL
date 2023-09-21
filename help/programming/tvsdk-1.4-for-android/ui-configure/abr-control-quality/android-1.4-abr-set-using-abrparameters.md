---
description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
title: Aangepaste bitsnelheden configureren met behulp van ABRControlParameters
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Aangepaste bitsnelheden configureren met behulp van ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.

Voor `ABRControlParameters`:

* U moet waarden opgeven voor alle parameters tijdens de constructietijd.
* U kunt afzonderlijke waarden niet wijzigen na de constructietijd.
* Als de parameters die u opgeeft, zich buiten het toegestane bereik bevinden, `ArgumentError` wordt gegenereerd.

1. Bepaal aanvankelijke, minimum, en maximumbeetjetarieven.
1. Bepaal het beleid ABR:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. De ABR-parameterwaarden instellen in het dialoogvenster `ABRControlParameters` en deze aan de Media Player toewijzen.

   ```java
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```
