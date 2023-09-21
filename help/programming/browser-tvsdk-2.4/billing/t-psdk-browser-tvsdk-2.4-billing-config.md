---
description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
title: Factureringsmetriek configureren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Factureringsmetriek configureren{#configure-billing-metrics}

Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.

De meeste klanten zouden de standaardconfiguratie moeten gebruiken.

>[!IMPORTANT]
>
>De configuratie die u instelt, blijft van kracht gedurende de levensduur van de mediaspeler. Nadat u de mediaspeler hebt geïnitialiseerd, kunt u de configuratie niet meer wijzigen.

Factureringsmetriek vormen:

* Voer het volgende codevoorbeeld in.

  ```js
  var config = new AdobePSDK.MediaPlayerItemConfig(); 
  config.billingMetricsConfiguration.isEnabled = true; 
  config.billingMetricsConfiguration.proVODBillableDurationMinutes = 60; 
  config.billingMetricsConfiguration.stdVODBillableDurationMinutes = 30; 
  config.billingMetricsConfiguration.liveBillableDurationMinutes = 15; 
  _player.replaceCurrentResource(_resource, config);
  ```

  waar `_player` is een instantie van `AdobePSDK.MediaPlayer` en `_resource` is een instantie van `AdobePSDK.MediaResource`.
