---
description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
title: Aangepaste bitsnelheden configureren met ABRControlParameters
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Aangepaste bitsnelheden configureren met ABRControlParameters {#configure-adaptive-bit-rates-using-abrcontrolparameters}

U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.

Voor `ABRControlParameters` gelden de volgende voorwaarden:

* Tijdens de constructie moet u waarden opgeven voor alle parameters.
* Na de constructie kunt u geen afzonderlijke waarden wijzigen.
* Als de parameters die u opgeeft buiten het toegestane bereik vallen, wordt een `ArgumentError` gegenereerd.

1. Bepaal uw aanvankelijke, minimum, en maximumbeetjetarieven.
1. Bepaal het beleid ABR:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Stel de ABR-parameterwaarden in de constructor `ABRControlParameters` in en wijs de waarden toe aan de Media Player.

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
