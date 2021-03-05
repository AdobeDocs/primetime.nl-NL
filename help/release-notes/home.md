---
title: Opmerkingen bij de release Primetime
seo-title: Opmerkingen bij de release van Adobe Primetime
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: a42c5b4478967822c920d96b05d5f04a6dec8c25
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Opmerkingen bij de release Primetime

Welkom bij de Adobe Primetime Release Notes. De documenten die in de linkernavigatie worden vermeld verstrekken versie-specifieke informatie, systeemvereisten, beperkingen, vaste kwesties, en bekende kwesties.

## Verbeteringen en correcties in PTAI 21.2.2

De release bevat ondersteuning voor het invoegen/synchroniseren van EXT-X-IMAGE-STREAM-INF-streams in HLS-streams. De eigenschap wordt toegelaten door een server-zijconfiguratie. Neem contact op met de vertegenwoordiger van uw technische account om deze functie in te schakelen.

## Oplossingen in TVSDK 3.13 Android

Deze release biedt een oplossing voor het probleem van het stilzetten van de Widevine DRM-stream of het tonen van zwarte frames op ABR-apparaten op FireTV, waaronder Fire TV-apparaten van de derde generatie en Fire TV-apparaten van de eerste en tweede generatie.

Stel de API `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` voor de opgegeven Fire TV-apparaten in voordat u het afspelen start om het probleem op te lossen. De standaardwaarde is false.

Raadpleeg [TVSDK voor opmerkingen bij de Android-release](../release-notes/tvsdk-3x-android.md) voor meer informatie.

## Verbeteringen en correcties in Opmerkingen bij de release TVSDK 3.12 iOS

De release was vooral gericht op het oplossen van problemen met klanten.

Zie voor meer informatie over de huidige uitgebrachte versie voor [iOS](../release-notes/tvsdk-3x-ios.md).

## Zie ook

| Handboek | Beschrijving |
|--- |--- |
| [Help bij programmeren bij primetime](/help/programming/home.md) | Hiermee kunt u leren toepassingen en videospelers te ontwikkelen met behulp van Java op Android-apparaten en met behulp van doelstelling-C op iOS-apparaten. |
| [Help bij Primetime-migratie en -conversie](/help/migration-guides/home.md) | Verklaart het omzettings en migratieproces om van uw bestaande Reeks van de TVSDK van Primetime aan de volgende-generatiereeks over te gaan. |
| [Referentie-implementatie](/help/android-reference-implementation/home.md) | Helpt de TVSDK te begrijpen en de functies te wijzigen om uw persoonlijke speler aan te passen. |
| [Primetime-API-verwijzingen](/help/reference/api-references.md) | Verstrekt gedetailleerde informatie over functies TVSDK, gegevensstructuren en andere programmeringsconcepten. |
| [Digital Rights Management](/help/digital-rights-management/home.md) | Helpt u meer over diverse gebruikersscenario&#39;s in Digital Rights Management (DRM) te leren |
| [Help bij primetime Ad Insertion](/help/primetime-ad-insertion/home.md) | Verklaart hoe te om inhoud te monetiseren door gebruiker-gerichte dynamische advertenties op de server op te nemen en publiek met gepersonaliseerde advertenties in dienst te nemen. |
| [Archieven](https://helpx.adobe.com/primetime/archives.html) | Download PDF&#39;s van de gearchiveerde documentatie. |

## Nuttige bronnen

* [Get to Know Adobe Primetime](https://www.adobe.com/in/marketing/primetime.html)

* [Gelijktijdige bewaking](https://tve.helpdocsonline.com/concurrency-monitoring-introduction)

* [Primetime-verificatie](https://tve.helpdocsonline.com/home)

* [Adobe Primetime DRM-forums](https://forums.adobe.com/community/adobe_access)

* [Adobe Primetime Developer Resources](https://www.adobe.com/devnet/primetime.html)
