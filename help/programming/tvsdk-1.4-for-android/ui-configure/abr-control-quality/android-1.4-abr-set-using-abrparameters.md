---
description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
seo-description: U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.
seo-title: Aangepaste bitsnelheden configureren met ABRControlParameters
title: Aangepaste bitsnelheden configureren met ABRControlParameters
uuid: c877c5cc-ad72-46dc-afc4-d41ee097a9a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Aangepaste bitsnelheden configureren met ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}

U kunt waarden voor ABR-besturingselementen alleen instellen met ABRControlParameters, maar u kunt op elk gewenst moment een nieuwe waarde maken.

Voor `ABRControlParameters` gelden de volgende voorwaarden:

* U moet waarden opgeven voor alle parameters tijdens de constructietijd.
* U kunt afzonderlijke waarden niet wijzigen na de constructietijd.
* Als de parameters die u opgeeft buiten het toegestane bereik vallen, wordt een `ArgumentError` gegenereerd.

1. Bepaal aanvankelijke, minimum, en maximumbeetjetarieven.
1. Bepaal het beleid ABR:

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. Stel de ABR-parameterwaarden in de constructor `ABRControlParameters` in en wijs deze toe aan Mediaspeler.

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

