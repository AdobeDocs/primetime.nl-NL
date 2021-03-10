---
description: U kunt aangepaste tagnamen in TVSDK globaal configureren met de klasse PTSDKConfig.
title: Methoden van de klasse Config voor tags
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Methoden van de klasse Config voor tags{#config-class-methods-for-tags}

U kunt aangepaste tagnamen in TVSDK globaal configureren met de klasse PTSDKConfig.

TVSDK past de algemene configuratie automatisch toe op elke mediastream waarvoor geen streamspecifieke configuratie is opgegeven.

`PTSDKConfig` stelt deze methoden beschikbaar voor het beheer van aangepaste tags:

| **Abonneren op specifieke aangepaste tags** |
|---|
| `subscribedTags` | Hiermee wordt de huidige lijst met geabonneerde tags opgehaald. |
| `setSubscribedTags` | Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld. |
| **De advertentietags aanpassen die worden gebruikt door de standaardopportuniteitsdetector** |
| `adTags` | Hiermee wordt de huidige lijst met advertentietags opgehaald. |
| `setAdTags` | Hiermee stelt u de lijst met advertentietags in die door de standaardopportuniteitsgenerator wordt gebruikt. |

Houd rekening met het volgende:

* De settermethoden staan niet toe dat de tagparameter null-waarden bevat.
* De naam van de aangepaste tag moet het voorvoegsel # bevatten.

   #EXT-X-ASSET is bijvoorbeeld een correcte aangepaste tagnaam, maar EXT-X-ASSET is onjuist.
* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.

