---
description: 'null'
seo-description: 'null'
seo-title: Bloklijst van toepassingsruntimes
title: Bloklijst van toepassingsruntimes
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Bloklijst van toepassingsruntimes{#blocklist-of-application-runtimes}

De bloklijst met toepassingsruntimes geeft de versie van de Primetime-client of Flash Runtime aan die geen toegang heeft tot inhoud. Geef de beperkte runtime (Flash Player, AIR of iOS), het platform en de versie op.

Voorbeeld van gebruik: Net als in de bloklijst Primetime DRM-client kan de nieuwste versie van de runtimes van Flash Player, AIR of iOS worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud.

Naast de volgende kenmerken kunt u de toepassingsruntime identificeren aan de hand van de kenmerken die worden ondersteund voor Primetime DRM-clientversies:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Toepassing | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exacte overeenkomst | Hiermee wordt de naam van de runtime van de toepassing aangegeven. |

