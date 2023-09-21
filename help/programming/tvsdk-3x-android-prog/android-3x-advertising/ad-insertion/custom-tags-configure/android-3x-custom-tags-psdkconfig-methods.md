---
description: U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.
title: Methoden van de klasse Config voor tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Methoden van de klasse Config voor tags {#config-class-methods-for-tags}

U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.

TVSDK past automatisch de globale configuratie op om het even welke media stroom toe die geen stroom-specifieke configuratie specificeert.

`MediaPlayerItemConfig` stelt deze methoden beschikbaar voor het beheer van aangepaste tags:

**Abonneren op specifieke aangepaste tags**

| <b>Methode</b> | <b>Beschrijving</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | Hiermee wordt de huidige lijst met geabonneerde tags opgehaald. |
| `public final void setSubscribedTags(String[] tags);` | Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld.  Uw toepassing wordt ook automatisch geabonneerd op alle tags die via `setAdTags`. |

**De advertentietags aanpassen die worden gebruikt door de standaardopportuniteitsdetector**

| <b>Methode</b> | <b>Beschrijving</b> |
|--- |--- |
| `public final String[] getAdTags;` | Hiermee wordt de huidige lijst met advertentietags opgehaald. |
| `public final void setAdTags(String[] tags);` | Hiermee stelt u de lijst met advertentietags in die door de standaardopportuniteitsgenerator wordt gebruikt. |

Houd rekening met het volgende:

* De settermethoden staan niet toe dat de tagparameter null-waarden bevat.

  Indien aangetroffen, genereert TVSDK een `IllegalArgumentException`.
* De aangepaste tagnaam moet de `#` voorvoegsel

  Bijvoorbeeld: `#EXT-X-ASSET` is een correcte aangepaste tagnaam, maar `EXT-X-ASSET` is onjuist.

* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.
