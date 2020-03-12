---
description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
seo-description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
seo-title: Aangepaste bitsnelheden configureren met ABRControlParameters
title: Aangepaste bitsnelheden configureren met ABRControlParameters
uuid: 7084e954-196b-492e-846f-f8b36bed13a9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Aangepaste bitsnelheden configureren met ABRControlParameters {#configure-adaptive-bit-rates-using-abrcontrolparameters}

U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.

De volgende voorwaarden zijn van toepassing op `ABRControlParameters`:

* Tijdens de constructie moet u waarden opgeven voor alle parameters.
* Na de constructie kunt u geen afzonderlijke waarden wijzigen.
* Als de parameters die u opgeeft buiten het toegestane bereik vallen, `ArgumentError` wordt een fout gegenereerd.

1. Bepaal uw aanvankelijke, minimum, en maximumbeetjetarieven.
1. Bepaal het beleid ABR:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Stel de ABR-parameterwaarden in de `ABRControlParameters` constructor in en wijs de waarden toe aan de Media Player.

   ```
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```

