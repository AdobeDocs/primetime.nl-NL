---
description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw Adobe Enablement vertegenwoordiger hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
title: Factureringsmetriek configureren
exl-id: 1eb50822-77a0-4b3a-a84c-b6082bcd1cad
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Factureringsmetriek configureren{#configure-billing-metrics}

Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw Adobe Enablement vertegenwoordiger hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.

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
