---
title: Lijst van gewezen personen van toepassingsruntimes
description: Lijst van gewezen personen van toepassingsruntimes
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Lijst van gewezen personen van toepassingsruntimes {#blocklist-of-application-runtimes}

Lijst van gewezen personen van toepassingsruntimes specificeert de versie van de cliënt Primetime of Flash Runtime die tot inhoud niet kan toegang hebben. Geef de beperkte runtime (Flash Player, AIR of iOS), het platform en de versie op.

Voorbeeld van gebruik: Net als bij de Primetime DRM Client lijst van gewezen personen kan de nieuwste versie van de Flash Player-, AIR- of iOS-runtimes worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud.

Naast de volgende kenmerken kunt u de toepassingsruntime identificeren aan de hand van de kenmerken die worden ondersteund voor Primetime DRM-clientversies:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Toepassing | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exacte overeenkomst | Hiermee wordt de naam van de runtime van de toepassing aangegeven. |

