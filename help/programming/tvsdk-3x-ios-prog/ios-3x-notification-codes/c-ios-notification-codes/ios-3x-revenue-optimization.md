---
description: Deze tabel bevat gedetailleerde informatie over meldingen voor de optimalisatie van inkomsten.
title: ONTVANGSTEN Optimalisatie
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# ONTVANGSTEN Optimalisatie {#revenue-optimization-code}

Deze tabel bevat gedetailleerde informatie over OPTIMALISATIEmeldingen voor ONTVANGSTEN.

## Enable Revenue Optimization Reporting {#enable-revenue-optimization-reporting}

Gebruik de API PTMediaPlayer om deze rapportage in te schakelen: `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>De meeste informatieve meldingen bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

| Code | Naam | Melding binnen | Metagegevenstoetsen | Opmerkingen |
|---|---|---|---|---|
| 401001 | REVENUE_OPTIMIZATION_REPORTING | Geen | Verwijs hieronder lijst voor meta-gegevenssleutels die op verschillende gebeurtenissen worden gebaseerd. | Geen |

| Gebeurtenisdetails | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_START** Wordt verzonden in TVSDK wanneer MediaPlayer::replaceCurrentResource wordt aangeroepen. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, event, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAndLoading, resourceType RepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_START** Wordt verzonden in TVSDK wanneer de inhoud is voorbereid en klaar is voor afspelen. Deze gebeurtenis wordt niet verzonden bij elke manifestupload. Wordt alleen verzonden bij de eerste laadbewerking. | clientTimestamp, contentURL, contentType, event, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Wordt verzonden in TVSDK wanneer een opportuniteit wordt gegenereerd. | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_START** Wordt verzonden in TVSDK wanneer een opportuniteit begint op te lossen. | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Wordt verzonden in TVSDK wanneer een advertentieoplosser MediaPlayerClient::notifyFailed() aanroept. Gegevens moeten worden ingevuld | opportunityId, notificationAD |
| **AD_RESOURCE_LOAD** Wordt verzonden wanneer een advertentiemiddel via URL wordt opgehaald. responseStartTime:Unix timestamp voor wanneer het verzoek eerst begon. responseTotalTime:Totale hoeveelheid tijd (in seconden) die het voor een reactie aan lading nam. responseStatus:De statuscode die tijdens het ophalen van de bron wordt aangetroffen. status:&quot;error&quot; of &quot;success&quot; referenceAdId:De verwijzende en id die opvragen van deze resource (indien aanwezig). referenceUrl: De verwijzende url die om het halen van deze bron verzocht. errorMessage:If the status is &quot;error&quot;, the reason for the error will be located here. | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referenceURL, referenceAdId |
| **AD_RESOURCE_LOAD_CRS** Wordt verzonden in TVSDK wanneer een CRS wordt toegepast op een middel, en de respons voor m3u8. resourceType:altijd &quot;crs&quot;. responseStartTime:Unix timestamp voor wanneer het verzoek eerst begon. responseTotalTime:Totale hoeveelheid tijd (in seconden) die het voor een reactie aan lading nam. responseStatus:De statuscode die tijdens het ophalen van de bron wordt aangetroffen. status: &quot;error&quot; of &quot;success&quot;. errorMessage:If the status is &quot;error&quot;, the reason for the error will be located here. mediaFileUrl:De oorspronkelijke URL van het mediabestand die is geselecteerd. mediaFileBitrate:De bitsnelheid van het mediabestand dat is geselecteerd. mediaFileMimeType: het mime-type van het mediabestand dat is geselecteerd. url:De URL van het laatste element. | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** Wordt verzonden in TVSDK nadat een addBreak op de tijdlijn is geplaatst. Deze gebeurtenis vindt één keer plaats voor elk ad-einde. proposedTime:The time in which the ad break was requested to be placed. actualTime:De tijd waarin het advertentieeinde daadwerkelijk is geplaatst. proposedDuration:De duur van het ad-einde dat werd gevraagd om in te voegen. Voor live-inhoud is dit de actieduur. Voor VOD-inhoud is dit normaal -1. actualDuration:De werkelijke duur van het ingevoegde ad-einde. Berekend als de totale duur van alle advertenties, gedefinieerd door de respectieve segmentduur, toegevoegd of vervangen in de oorspronkelijke streamtijdlijn. proposedAds:The number of ads in the proposed ad break. totalAds:Het aantal advertenties dat is geplaatst. advertenties...n:De gelukte advertenties worden hier ingevoegd. De volledige en duidelijke informatie kan van AD_OPPORTUNITY_RESOLVE_PROCESS worden teruggewonnen | opportunityId, status, errorMessage, proposedTime, proposedDuration, actualTime, actualDuration, proposedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_START** Wordt verzonden in TVSDK nadat een advertentie wordt afgespeeld. | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** Wordt verzonden in TVSDK nadat een advertentie is afgespeeld. | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **ADBREAK_PLAYBACK_START** Wordt verzonden in TVSDK wanneer het afspelen van een bijschrift begint. | clientTimestamp, event, opportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** Wordt verzonden in TVSDK wanneer het afspelen is voltooid. | clientTimestamp, event, opportunityId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Wordt verzonden in TVSDK wanneer inhoud is voltooid. Dit kan gebeuren als de stream wordt vervangen, de speler een foutstatus invoert, de speler opnieuw wordt ingesteld of de inhoud daadwerkelijk wordt voltooid. Deze gebeurtenis zal noodzakelijk zijn om sessionId te volgen. | clientTimestamp, event, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Wordt verzonden in TVSDK wanneer een advertentie een fout bevat bij het afspelen (fout in de variantstream). | gebeurtenis, fout, tijdstempel, manifestUrl, tijd, opportunityId, url |
