---
description: 'Deze tabel bevat gedetailleerde informatie over meldingen voor de optimalisatie van inkomsten. '
seo-description: 'Deze tabel bevat gedetailleerde informatie over meldingen voor de optimalisatie van inkomsten. '
seo-title: Code ONTVANGSTEN
title: Code ONTVANGSTEN
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Code ONTVANGSTEN {#revenue-optimization-code}

Deze tabel bevat gedetailleerde informatie over OPTIMALISATIEmeldingen voor ONTVANGSTEN.

## Enable Revenue Optimization Reporting {#enable-revenue-optimization-reporting}

Gebruik de API PTMediaPlayer om deze rapportage in te schakelen: `[mediaPlayer
setRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

[!NOpmerking]: De meeste informatieve meldingen bevatten relevante metagegevens, bijvoorbeeld de URL van de bron die niet is gedownload. Sommige meldingen bevatten metagegevens om op te geven of het probleem is opgetreden in de hoofdvideo-inhoud, in de alternatieve audio-inhoud of in een advertentie.

|Code|Naam|Melding binnen|Metagegevenstoetsen|Opmerkingen||—|—|—|—|—||401001| ONTVANGSTEN_OPTIMALISATIE_RAPPORTERING| Geen| Verwijs hieronder lijst voor meta-gegevenssleutels die op verschillende gebeurtenissen worden gebaseerd. | Geen|

| Gebeurtenisdetails | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_START** Verzonden in TVSDK wanneer MediaPlayer::replaceCurrentResource wordt geroepen. | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, event, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adRequestTimeout, delayAndLoading, resourceType RepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_START** Verzonden in TVSDK wanneer de inhoud de voorbereide staat is ingegaan en klaar voor playback is. Deze gebeurtenis wordt niet verzonden bij elke manifestupload. Wordt alleen verzonden bij de eerste laadbewerking. | clientTimestamp, contentURL, contentType, event, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** Wordt verzonden in TVSDK wanneer een opportuniteit wordt gegenereerd. | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_START** Verzonden in TVSDK wanneer een kans begint op te lossen. | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** Wordt verzonden in TVSDK wanneer een advertentieconverteerder MediaPlayerClient::notifyFailed() aanroept. Gegevens moeten worden ingevuld | opportunityId, notificationAD |
| **AD_RESOURCE_LOAD** Verzonden wanneer om het even welke hulpbron door URL wordt opgehaald. responseStartTime:Unix timestamp voor wanneer het verzoek eerst begon. responseTotalTime:Totale hoeveelheid tijd (in seconden) die het voor een reactie aan lading nam. responseStatus:De statuscode aangetroffen tijdens het ophalen van de bron. status:&quot;error&quot; of &quot;success&quot; referenceAdId:De verwijzende en id die opvragen van deze resource (indien aanwezig). referenceUrl: De verwijzende url die om het halen van deze bron verzocht. errorMessage:If the status is &quot;error&quot;, the reason for the error will be located here. | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referenceURL, referenceAdId |
| **AD_RESOURCE_LOAD_CRS** Verzonden in TVSDK wanneer CRS op activa wordt toegepast, evenals de reactie voor m3u8. resourceType:altijd &quot;crs&quot;. responseStartTime:Unix timestamp voor wanneer het verzoek eerst begon. responseTotalTime:Totale hoeveelheid tijd (in seconden) die het voor een reactie aan lading nam. responseStatus:De statuscode aangetroffen tijdens het ophalen van de bron. status: &quot;error&quot; of &quot;success&quot;. errorMessage:If the status is &quot;error&quot;, the reason for the error will be located here. mediaFileUrl:De oorspronkelijke URL van het mediabestand die is geselecteerd. mediaFileBitrate:De bitsnelheid van het mediabestand dat is geselecteerd. mediaFileMimeType: Het mime-type van het mediabestand dat is geselecteerd. url:De URL van het laatste element. | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** Wordt verzonden in TVSDK nadat een adBreak op de tijdlijn is geplaatst. Deze gebeurtenis vindt één keer plaats voor elk ad-einde. proposedTime:The time in which the ad break was requested to be placed. actualTime:De tijd waarin het advertentieeinde daadwerkelijk is geplaatst. proposedDuration:De duur van het ad-einde dat werd gevraagd om in te voegen. Voor live-inhoud is dit de actieduur. Voor VOD-inhoud is dit normaal -1. actualDuration:De werkelijke duur van het ingevoegde ad-einde. Berekend als de totale duur van alle advertenties, gedefinieerd door de respectieve segmentduur, toegevoegd of vervangen in de oorspronkelijke streamtijdlijn. proposedAds:The number of ads in the proposed ad break. totalAds:Het aantal advertenties dat is geplaatst. advertenties...znw:De gelukte invoegadvertenties worden hier ingevoegd. De volledige en duidelijke informatie kan van AD_OPPORTUNITY_RESOLVE_PROCESS worden teruggewonnen | opportunityId, status, errorMessage, proposedTime, proposedDuration, actualTime, actualDuration, proposedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_START** Wordt verzonden in TVSDK nadat een advertentie wordt afgespeeld. | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** Wordt verzonden in TVSDK nadat een advertentie is afgespeeld. | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **ADBREAK_PLAYBACK_START** Wordt verzonden in TVSDK wanneer het afspelen van een bijschrift wordt gestart. | clientTimestamp, event, opportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** Wordt verzonden in TVSDK wanneer het afspelen van een bijschrift is voltooid. | clientTimestamp, event, opportunityId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** Wordt verzonden in TVSDK wanneer inhoud wordt voltooid. Dit kan voorkomen als de stream wordt vervangen, de speler een foutstatus invoert, de speler opnieuw wordt ingesteld of de inhoud daadwerkelijk wordt voltooid. Deze gebeurtenis zal noodzakelijk zijn om sessionId te volgen. | clientTimestamp, event, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** Verzonden in TVSDK wanneer een advertentie een fout die (de fouten van de variantstroom) speelt heeft. | gebeurtenis, fout, tijdstempel, manifestUrl, tijd, opportunityId, url |