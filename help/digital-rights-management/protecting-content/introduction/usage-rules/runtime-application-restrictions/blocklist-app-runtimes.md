---
title: Lijst van gewezen personen van toepassingsruntimes
description: Lijst van gewezen personen van toepassingsruntimes
copied-description: true
exl-id: f8d1d385-41d4-4361-82c1-417b2ff421c5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Lijst van gewezen personen van toepassingsruntimes {#blocklist-of-application-runtimes}

Lijst van gewezen personen van toepassingsruntimes specificeert de versie van de cliënt Primetime of Flash Runtime die tot inhoud niet kan toegang hebben. Geef de beperkte runtime (Flash Player, AIR of iOS), het platform en de versie op.

Voorbeeld van gebruik: Net als bij de Primetime DRM Client lijst van gewezen personen kan de nieuwste versie van de runtimes van de Flash Player, AIR of iOS worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud.

Naast de volgende kenmerken kunt u de toepassingsruntime identificeren aan de hand van de kenmerken die worden ondersteund voor Primetime DRM-clientversies:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Toepassing | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Exacte overeenkomst | Hiermee wordt de naam van de runtime van de toepassing aangegeven. |
