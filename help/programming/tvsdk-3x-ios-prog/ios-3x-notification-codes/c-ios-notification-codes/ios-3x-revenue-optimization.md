---
description: 'Deze tabel bevat gedetailleerde informatie over meldingen voor de optimalisatie van inkomsten. '
seo-description: 'Deze tabel bevat gedetailleerde informatie over meldingen voor de optimalisatie van inkomsten. '
seo-title: Code ONTVANGSTEN
title: Code ONTVANGSTEN
translation-type: tm+mt
source-git-commit: df3d60874701383325be1afdd1ec5fe036f855f8
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---


# ONTVANGSTEN Optimalisatie code {#revenue-optimization-code}

Deze tabel bevat gedetailleerde informatie over OPTIMALISATIEmeldingen voor ONTVANGSTEN.

## Rapportage voor optimalisatie van inkomsten {#enable-revenue-optimization-reporting} inschakelen

Gebruik de API PTMediaPlayer om deze rapportage in te schakelen: `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>De meeste informatieve meldingen bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

| Code | Naam | Melding binnen | Metagegevenstoetsen | Opmerkingen |
|---|---|---|---|---|
| 401001 | REVENUE_OPTIMIZATION_REPORTING | Geen | Verwijs hieronder lijst voor meta-gegevenssleutels die op verschillende gebeurtenissen worden gebaseerd. | Geen |

| Gebeurtenisdetails | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_** STARTDispatched in TVSDK wanneer MediaPlayer::replaceCurrentResource wordt geroepen. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, event, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAndLoading, resourceType RepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_** STARTD wordt verzonden in TVSDK wanneer de inhoud de voorbereide status heeft bereikt en klaar is voor afspelen. Deze gebeurtenis wordt niet verzonden bij elke manifestupload. Wordt alleen verzonden bij de eerste laadbewerking. | clientTimestamp, contentURL, contentType, event, isLive, clientID |
| **AD_OPPORTUNITY_** GENERATEDDestre in TVSDK wanneer een kans wordt geproduceerd. | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_** STARTDestreheerd in TVSDK wanneer een kans begint op te lossen. | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_** FAILEDDeviste in TVSDK wanneer een advertentieresoluver MediaPlayerClient::notifyFailed() aanroept. Gegevens moeten worden ingevuld | opportunityId, notificationAD |
| **AD_RESOURCE_** LOADDispatched when any ad resource is fetched by URL. responseStartTime:Unix timestamp voor wanneer het verzoek eerst begon. responseTotalTime:Totale hoeveelheid tijd (in seconden) die het voor een reactie aan lading nam. responseStatus:De statuscode aangetroffen tijdens het ophalen van de bron. status:&quot;error&quot; of &quot;success&quot; referenceAdId:De verwijzende en id die opvragen van deze resource (indien aanwezig). referenceUrl: De verwijzende url die om het halen van deze bron verzocht. errorMessage:If the status is &quot;error&quot;, the reason for the error will be located here. | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referenceURL, referenceAdId |
| **AD_RESOURCE_LOAD_** CRSDispatched in TVSDK wanneer een CRS wordt toegepast op een middel, evenals de reactie voor m3u8. resourceType:altijd &quot;crs&quot;. responseStartTime:Unix timestamp voor wanneer het verzoek eerst begon. responseTotalTime:Totale hoeveelheid tijd (in seconden) die het voor een reactie aan lading nam. responseStatus:De statuscode aangetroffen tijdens het ophalen van de bron. status: &quot;error&quot; of &quot;success&quot;. errorMessage:If the status is &quot;error&quot;, the reason for the error will be located here. mediaFileUrl:De oorspronkelijke URL van het mediabestand die is geselecteerd. mediaFileBitrate:De bitsnelheid van het mediabestand dat is geselecteerd. mediaFileMimeType: Het mime-type van het mediabestand dat is geselecteerd. url:De URL van het laatste element. | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_** PLACEDVerzonden in TVSDK nadat een adBreak op de chronologie werd geplaatst. Deze gebeurtenis vindt één keer plaats voor elk ad-einde. proposedTime:The time in which the ad break was requested to be placed. actualTime:De tijd waarin het advertentieeinde daadwerkelijk is geplaatst. proposedDuration:De duur van het ad-einde dat werd gevraagd om in te voegen. Voor live-inhoud is dit de actieduur. Voor VOD-inhoud is dit normaal -1. actualDuration:De werkelijke duur van het ingevoegde ad-einde. Berekend als de totale duur van alle advertenties, gedefinieerd door de respectieve segmentduur, toegevoegd of vervangen in de oorspronkelijke streamtijdlijn. proposedAds:The number of ads in the proposed ad break. totalAds:Het aantal advertenties dat is geplaatst. advertenties...znw:De gelukte invoegadvertenties worden hier ingevoegd. De volledige en duidelijke informatie kan van AD_OPPORTUNITY_RESOLVE_PROCESS worden teruggewonnen | opportunityId, status, errorMessage, proposedTime, proposedDuration, actualTime, actualDuration, proposedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_** STARTD wordt verzonden in TVSDK nadat een advertentie wordt afgespeeld. | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **AD_PLAYBACK_** COMPLETEDWordt verzonden in TVSDK nadat een advertentie is afgespeeld. | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **ADBREAK_PLAYBACK_** STARTD wordt verzonden in TVSDK wanneer het afspelen van een bijschrift wordt gestart. | clientTimestamp, event, opportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_** COMPLETEDVerzonden in TVSDK wanneer het afspelen van een update is voltooid. | clientTimestamp, event, opportunityId, clientId |
| **CONTENT_PLAYBACK_** COMPLETEDsend in TVSDK wanneer om het even welke inhoud wordt voltooid. Dit kan voorkomen als de stroom wordt vervangen, de speler een foutenstaat ingaat, de speler wordt teruggesteld, of de inhoud eigenlijk voltooit. Deze gebeurtenis zal noodzakelijk zijn om sessionId te volgen. | clientTimestamp, event, clientId, url, status, errorMessage |
| **AD_PLAYBACK_** ERRORDVerzonden in TVSDK wanneer een advertentie een fout speelt (de fouten van de variantstroom). | gebeurtenis, fout, tijdstempel, manifestUrl, tijd, opportunityId, url |
