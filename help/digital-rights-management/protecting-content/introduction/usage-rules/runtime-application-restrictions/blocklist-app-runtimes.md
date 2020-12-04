---
description: 'null'
seo-description: 'null'
seo-title: Lijst van afgewezen personen van toepassingsruntimes
title: Lijst van afgewezen personen van toepassingsruntimes
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Lijst van afgewezen personen van toepassingsruntimes {#blocklist-of-application-runtimes}

Lijst van afgewezen personen van toepassingsruntimes specificeert de versie van de cliënt Primetime of Flash Runtime die tot inhoud niet kan toegang hebben. Geef de beperkte runtime (Flash Player, AIR of iOS), het platform en de versie op.

Voorbeeld van gebruik: Net als bij de Primetime DRM Client lijst van afgewezen personen kan de nieuwste versie van de Flash Player-, AIR- of iOS-runtimes worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud.

Naast de volgende kenmerken kunt u de toepassingsruntime identificeren aan de hand van de kenmerken die worden ondersteund voor Primetime DRM-clientversies:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Toepassing | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exacte overeenkomst | Hiermee wordt de naam van de runtime van de toepassing aangegeven. |

