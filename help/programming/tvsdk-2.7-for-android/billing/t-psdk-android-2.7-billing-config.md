---
description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw Adobe Enablement vertegenwoordiger hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
title: Factureringsmetriek configureren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Factureringsmetriek {#configure-billing-metrics} vormen

Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw Adobe Enablement vertegenwoordiger hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.

>[!TIP]
>
>De meeste klanten zouden de standaardconfiguratie moeten gebruiken.

>[!IMPORTANT]
>
>De configuratie die u instelt, blijft van kracht gedurende de levensduur van de mediaspeler. Nadat u de mediaspeler hebt geïnitialiseerd, kunt u de configuratie niet meer wijzigen.

Factureringsmetriek vormen:

1. Voer het volgende codevoorbeeld in.

   ```java
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   BillingMetricsConfiguration billingConfig = new BillingMetricsConfiguration(); 
   billingConfig.setEnabled(true); 
   billingConfig.setProVODBillableDurationMinutes(60); 
   billingConfig.setStdVODBillableDurationMinutes(30); 
   billingConfig.setLiveBillableDurationMinutes(15); 
   config.setBillingMetricsConfiguration(billingConfig); 
   mediaPlayer.replaceCurrentResource(mediaResource, config);
   ```

