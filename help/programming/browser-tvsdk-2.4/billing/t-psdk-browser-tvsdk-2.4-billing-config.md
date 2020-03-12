---
description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
seo-description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
seo-title: Factureringsmetriek configureren
title: Factureringsmetriek configureren
uuid: 04d3b53e-f08c-49d0-ba42-5375f1307d2e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

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

   waarbij `_player` een instantie van `AdobePSDK.MediaPlayer` en een geval van `_resource` is `AdobePSDK.MediaResource`.

