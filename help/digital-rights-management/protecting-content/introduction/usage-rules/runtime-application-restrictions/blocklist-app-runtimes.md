---
title: Lijst van gewezen personen van toepassingsruntimes
description: Lijst van gewezen personen van toepassingsruntimes
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Lijst van gewezen personen van toepassingsruntimes {#blocklist-of-application-runtimes}

Lijst van gewezen personen van toepassingsruntimes specificeert de versie van de cliënt Primetime of Runtime van de Flash die tot inhoud niet kunnen toegang hebben. Geef de beperkte runtime (Flash Player, AIR of iOS), het platform en de versie op.

Voorbeeld: net als bij de Primetime DRM Client lijst van gewezen personen kan de nieuwste versie van de Flash Player-, AIR- of iOS-runtimes worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud.

Naast de volgende kenmerken kunt u de toepassingsruntime identificeren aan de hand van de kenmerken die worden ondersteund voor Primetime DRM-clientversies:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Toepassing | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exacte overeenkomst | Hiermee wordt de naam van de runtime van de toepassing aangegeven. |
