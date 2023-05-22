---
description: U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Primetime DRM-oplossing met Adobe.
keywords: DRM;DASH;HLS
title: Overzicht van de primaire DRM-interface
exl-id: e07c1551-5a9b-4907-94ea-6b7536918b91
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Overzicht van de primaire DRM-interface {#primetime-drm-interface-overview}

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

TVSDK geeft een `PTMediaPlayerItemDRMMetadataChanged` melding wanneer de DRM-metagegevens veranderen. Deze metagegevens worden gebruikt als invoer voor bijna alle functies van de `DRMManager` klasse.

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Als de DRM-beveiligde stream meerdere bitsnelheden (MBR) heeft gecodeerd, moeten de DRM-metagegevens die voor de afspeellijst van de variant worden gebruikt, gelijk zijn aan de metagegevens die in alle bitsnelheidstreams worden gebruikt.

>[!TIP]
>
>Wanneer u verwijst naar URL&#39;s met DRM-beveiligde elementen in uw iOS-app, wordt de parameter voor de queryreeks gebruikt `?faxs=1` moet worden toegevoegd aan de (MBR) set-level M3U8 URL. Bijvoorbeeld:

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

De `faxs=1` De parameter van het vraagkoord signaleert dat de inhoud DRM beschermd is, en brengt het DRM decryptiewerkschema dienovereenkomstig in iOS TVSDK in werking. U kunt ook de opdracht `faxs=1` tags toewijzen aan URL&#39;s met HLS-middelen die met DRM zijn beveiligd en die bestemd zijn voor andere platforms; het wordt waargenomen zoals vereist op iOS of behandeld als een non-op in spelers op andere platforms.

## Primetime DRM implementeren in een TSVDK-toepassing {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM is geïntegreerd in TVSDK, waardoor het implementeren van contentbeveiliging in een TVSDK-toepassing wordt vereenvoudigd.

Voor een overzicht en details over het gebruik van Primetime DRM om inhoudsbescherming in een toepassing van TVSDK uit te voeren, zie:

* [Adobe Primetime TVSDK-DRM Workflow (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)
