---
description: U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.
keywords: DRM;DASH;HLS
seo-description: U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.
seo-title: Overzicht van de primaire DRM-interface
title: Overzicht van de primaire DRM-interface
uuid: 5e794147-cc58-448c-b8ec-065e80ef01fd
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---


# Primetime DRM-interfaceoverzicht {#primetime-drm-interface-overview}

U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Neem contact op met uw Adobe voor de meest actuele informatie over de beschikbaarheid van DRM-oplossingen van derden.

Het belangrijkste client-side element van het DRM-systeem (Primetime Digital Rights Management) is DRM Manager.

Primetime DRM biedt een schaalbare, efficiënte workflow voor het implementeren van inhoudsbeveiliging in TVSDK-toepassingen. U beschermt en beheert de rechten voor uw video-inhoud door een licentie te maken voor elk digitaal mediabestand.

TVSDK ondersteunt de integratie van Primetime DRM als aangepaste DRM-workflows. Dit betekent dat uw toepassing de DRM-verificatieworkflows moet implementeren voordat de stream kan worden afgespeeld met de Flash DRMManager. Om dit in te schakelen, voorziet MediaPlayer u van DRM manager voor authentificatie.

Raadpleeg de DRM-voorbeeldspelercode in het TVSDK-pakket.

Dit zijn de belangrijkste API-elementen voor het werken met DRM:

* Een verwijzing in de mediaspeler naar het DRM-beheerobject dat het DRM-subsysteem implementeert:

   ```
   @property (readonly, nonatomic) DRMManager *drmManager
   ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

TVSDK geeft een `PTMediaPlayerItemDRMMetadataChanged`-melding weer wanneer de DRM-metagegevens veranderen. Deze metagegevens worden gebruikt als invoer voor bijna alle functies van de klasse `DRMManager`.

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Als de DRM-beveiligde stream meerdere bitsnelheden (MBR) heeft gecodeerd, moeten de DRM-metagegevens die voor de afspeellijst van de variant worden gebruikt, gelijk zijn aan de metagegevens die in alle bitsnelheidstreams worden gebruikt.

>[!TIP]
>
>Wanneer u verwijst naar URL&#39;s met DRM-beveiligde elementen in uw iOS-app, moet de parameter `?faxs=1` voor de queryreeks worden toegevoegd aan de (MBR)-URL op het niveau M3U8. Bijvoorbeeld:

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

De `faxs=1` parameter van het vraagkoord signaleert dat de inhoud DRM beschermd is, en brengt het DRM decryptiewerkschema dienovereenkomstig in iOS TVSDK in werking. U kunt de tag `faxs=1` ook toevoegen aan URL&#39;s met DRM-beveiligde HLS-elementen die bestemd zijn voor andere platforms. wordt waargenomen zoals vereist op iOS of behandeld als een non-op in spelers op andere platforms.

## Primetime DRM implementeren in een TSVDK-toepassing {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM is geïntegreerd in TVSDK, waardoor het implementeren van contentbeveiliging in een TVSDK-toepassing wordt vereenvoudigd.

Voor een overzicht en details over het gebruik van Primetime DRM om inhoudsbescherming in een toepassing van TVSDK uit te voeren, zie:

* [Adobe Primetime TVSDK-DRM Workflow (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)