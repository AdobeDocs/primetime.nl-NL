---
description: U kunt aangepaste tagnamen in TVSDK globaal configureren met de klasse PTSDKConfig.
seo-description: U kunt aangepaste tagnamen in TVSDK globaal configureren met de klasse PTSDKConfig.
seo-title: Methoden van de klasse Config voor tags
title: Methoden van de klasse Config voor tags
uuid: 27f1df0a-bbd3-4d80-820e-b659f2f33069
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Methoden van de klasse Config voor codes {#config-class-methods-for-tags}

U kunt aangepaste tagnamen in TVSDK globaal configureren met de klasse PTSDKConfig.

TVSDK past de algemene configuratie automatisch toe op elke mediastream waarvoor geen streamspecifieke configuratie is opgegeven.

`PTSDKConfig` stelt deze methoden beschikbaar voor het beheer van aangepaste tags:

| **Abonneren op specifieke aangepaste tags** |  |
|---|---|
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