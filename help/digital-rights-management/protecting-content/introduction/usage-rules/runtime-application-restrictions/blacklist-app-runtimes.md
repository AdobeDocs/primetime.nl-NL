---
description: 'null'
seo-description: 'null'
seo-title: Blacklist of application runtimes
title: Blacklist of application runtimes
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Blacklist of application runtimes{#blacklist-of-application-runtimes}

Blacklist of application runtimes specifies the version of the Primetime client or Flash Runtime that cannot access content. Geef de beperkte runtime (Flash Player, AIR of iOS), het platform en de versie op.

Voorbeeld van gebruik: Net als bij de zwarte lijst van de Primetime DRM-client kan de nieuwste versie van de Flash Player-, AIR- of iOS-runtimes worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud.

Naast de volgende kenmerken kunt u de toepassingsruntime identificeren aan de hand van de kenmerken die worden ondersteund voor Primetime DRM-clientversies:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Toepassing | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exacte overeenkomst | Hiermee wordt de naam van de runtime van de toepassing aangegeven. |

