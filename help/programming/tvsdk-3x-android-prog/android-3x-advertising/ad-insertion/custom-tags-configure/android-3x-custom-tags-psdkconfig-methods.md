---
description: U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.
seo-description: U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.
seo-title: Methoden van de klasse Config voor tags
title: Methoden van de klasse Config voor tags
uuid: b75aebac-4b94-4c42-bed4-3c17ad989cd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Methoden van de klasse Config voor tags {#config-class-methods-for-tags}

U kunt namen van aangepaste tags globaal configureren in TVSDK met de klasse MediaPlayerItemConfig.

TVSDK past automatisch de globale configuratie op om het even welke media stroom toe die geen stroom-specifieke configuratie specificeert.

`MediaPlayerItemConfig` stelt deze methoden beschikbaar voor het beheer van aangepaste tags:

**Abonneren op specifieke aangepaste tags**

| <b>Methode</b> | <b>Beschrijving</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | Hiermee wordt de huidige lijst met geabonneerde tags opgehaald. |
| `public final void setSubscribedTags(String[] tags);` | Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld.  Uw toepassing wordt ook automatisch geabonneerd op alle tags die via `setAdTags`worden verzonden. |

**De advertentietags aanpassen die worden gebruikt door de standaardopportuniteitsdetector**

| <b>Methode</b> | <b>Beschrijving</b> |
|--- |--- |
| `public final String[] getAdTags;` | Hiermee wordt de huidige lijst met advertentietags opgehaald. |
| `public final void setAdTags(String[] tags);` | Hiermee stelt u de lijst met advertentietags in die door de standaardopportuniteitsgenerator wordt gebruikt. |

Houd rekening met het volgende:

* De settermethoden staan niet toe dat de tagparameter null-waarden bevat.

   Indien aangetroffen, genereert TVSDK een `IllegalArgumentException`.
* De aangepaste tagnaam moet het `#` voorvoegsel bevatten.

   De aangepaste tagnaam `#EXT-X-ASSET` is bijvoorbeeld correct, maar `EXT-X-ASSET` is onjuist.

* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.