---
description: U kunt tijdbereiken in VOD-streams markeren, verwijderen en vervangen door verschillende combinaties van ad-signaalmodus en metagegevens te gebruiken. Verschillende combinaties van signalerende wijze en meta-gegevens resulteren in verschillend gedrag.
seo-description: U kunt tijdbereiken in VOD-streams markeren, verwijderen en vervangen door verschillende combinaties van ad-signaalmodus en metagegevens te gebruiken. Verschillende combinaties van signalerende wijze en meta-gegevens resulteren in verschillend gedrag.
seo-title: Effect op het toevoegen en verwijderen van gegevens uit de advertentiemodus en combinaties van metagegevens
title: Effect op het toevoegen en verwijderen van gegevens uit de advertentiemodus en combinaties van metagegevens
uuid: 49abab49-4e52-477d-b7ed-688ee63e7473
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Effect op het toevoegen en verwijderen van gegevens uit de advertentiemodus en de combinaties van metagegevens {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

U kunt tijdbereiken in VOD-streams markeren, verwijderen en vervangen door verschillende combinaties van ad-signaalmodus en metagegevens te gebruiken. Verschillende combinaties van signalerende wijze en meta-gegevens resulteren in verschillend gedrag.

>[!TIP]
>
>Wanneer er een conflict tussen tijdwaaiers en ad signalerende wijzen is, geeft TVSDK de prioriteit van tijdwaaiers.

De volgende lijst verstrekt de details over het signaleren wijze en gedrag van de meta-gegevenscombinatie:

**Servertoewijzing**

| **Metagegevens toevoegen** | **Gemaakte oplossingen** | **`PlacementInformations`gemaakt** | **Resulterend gedrag** |
|--- |--- |--- |--- |
|  | Verwijderen | Verwijderen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Verwijderde bereiken |
| Verwijderen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE),` <br>`PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Bereiken verwijderd, advertenties ingevoegd |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Toegevoegde advertenties |
| Vervangen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Vervangen bereiken |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Gemarkeerde bereiken |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Bereiken gemarkeerd, geen advertenties ingevoegd |

**Manifest Cues**

| Metagegevens toevoegen | Gemaakte oplossingen | `PlacementInformations` gemaakt | Resulterend gedrag |
|--- |--- |--- |--- |
| Auditude | Auditude | `PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Toegevoegde advertenties |
| Verwijderen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)`<br>`PlacementInfo (Type.PRE_ROLL, Mode.INSERT)` | Bereiken verwijderd, advertenties ingevoegd |
| Mark, Auditude | Mark, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Bereiken gemarkeerd, geen advertenties ingevoegd |
| Verwijderen | Verwijderen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Verwijderde bereiken |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Gemarkeerde bereiken |
| Vervangen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Vervangen bereiken |

**Aangepast tijdbereik**

| Metagegevens toevoegen | Gemaakte oplossingen | `PlacementInformations` gemaakt | Resulterend gedrag |
|--- |--- |--- |--- |
| Verwijderen | Verwijderen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Verwijderde bereiken |
| Verwijderen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Bereiken verwijderd, geen advertenties ingevoegd |
| Auditude | Auditude | Geen | Geen advertenties ingevoegd |
| Vervangen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Bereiken vervangen door advertenties |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Gemarkeerde bereiken |
| Mark, Auditude | Aangepaste advertentie, controle | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Bereiken gemarkeerd, geen advertenties ingevoegd |

**Niet ingesteld (standaard)**

| Metagegevens toevoegen | Gemaakte oplossingen | `PlacementInformations` gemaakt | Resulterend gedrag |
|--- |--- |--- |--- |
| Verwijderen | Verwijderen | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)` | Verwijderde bereiken |
| Verwijderen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Bereiken verwijderd, advertenties ingevoegd |
| Auditude | Auditude | `PlacementInfo (Type.SERVER_MAP, Mode.INSERT)` | Toegevoegde advertenties |
| Vervangen, Auditude | Verwijderen, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)` | Bereiken vervangen door advertenties |
| Mark | CustomAd | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Gemarkeerde bereiken |
| Mark, Auditude | CustomAd, Auditude | `PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)` | Gemarkeerde bereiken |