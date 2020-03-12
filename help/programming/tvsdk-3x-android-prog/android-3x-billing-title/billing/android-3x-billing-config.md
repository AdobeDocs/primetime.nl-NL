---
description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
seo-description: Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.
seo-title: Factureringsmetriek configureren
title: Factureringsmetriek configureren
uuid: 340439bf-185b-4761-a481-010908842811
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Factureringsmetriek configureren {#configure-billing-metrics}

Als u de standaardconfiguratie gebruikt, is er niets anders u moet doen om het factureren toe te laten of te vormen. Als u verschillende configuratieparameters van uw vertegenwoordiger van Adobe Enablement hebt verkregen, gebruik de klasse BillingMetricsConfiguration om deze parameters omhoog te plaatsen alvorens de media speler te initialiseren.

>[!TIP]
>
>De meeste klanten zouden de standaardconfiguratie moeten gebruiken.

>[!IMPORTANT]
>
>De configuratie die u instelt, blijft van kracht gedurende de levensduur van de mediaspeler. Nadat u de mediaspeler hebt geïnitialiseerd, kunt u de configuratie niet meer wijzigen.

Factureringsmetriek vormen:

Voer het volgende codevoorbeeld in.

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
