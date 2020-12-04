---
description: Wanneer een segment mist, bijvoorbeeld wanneer een bepaald segment er niet in slaagt te downloaden, probeert om door een verscheidenheid van failoverpogingen terug te krijgen. Als het niet kan herstellen, geeft het een fout uit.
seo-description: Wanneer een segment mist, bijvoorbeeld wanneer een bepaald segment er niet in slaagt te downloaden, probeert om door een verscheidenheid van failoverpogingen terug te krijgen. Als het niet kan herstellen, geeft het een fout uit.
seo-title: Ontbrekende segment-failover
title: Ontbrekende segment-failover
uuid: 17ee1221-e1eb-4f64-a406-4d7eff1d7555
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Ontbrekende segment failover{#missing-segment-failover}

Wanneer een segment mist, bijvoorbeeld wanneer een bepaald segment er niet in slaagt te downloaden, probeert om door een verscheidenheid van failoverpogingen terug te krijgen. Als het niet kan herstellen, geeft het een fout uit.

Als een segment ontbreekt op de server omdat, bijvoorbeeld, het manifestdossier niet aanwezig is, kan het segment niet worden gedownload, etc., probeert TVSDK om over te ontbreken door de volgende opties te proberen:

1. Poging tot failover aan het zelfde segment, aan de zelfde beetjetarief, in een variantdossier.
1. Schakel over naar een andere bitsnelheid (ABR-switch) in hetzelfde bestand.
1. Doorloop elke beschikbare bitsnelheid in elke beschikbare variant.
1. Sla het segment over en geef een waarschuwing weer.

Wanneer TVSDK geen alternatief segment kan verkrijgen, leidt het tot een `CONTENT_ERROR` foutenmelding. Deze melding bevat een binnenste melding met de code `DOWNLOAD_ERROR`. Als de stream met het probleem een alternatieve audiotrack is, wordt de foutmelding `AUDIO_TRACK_ERROR` gegenereerd.

Als de video-engine continu geen segmenten kan ophalen, beperkt het continue segmentoverslaan tot 5, waarna het afspelen wordt gestopt en een `NATIVE_ERROR` met code 5 wordt uitgegeven.

>[!NOTE]
>
>De adaptieve parameters van de beetjetarief (ABR) worden niet in overweging genomen wanneer een failover voorkomt. Dit komt doordat het failover-mechanisme is ontworpen om een van de momenteel beschikbare afspeellijsten, ongeacht hun bitsnelheidprofiel, te gebruiken als back-upstreams.
>
>Tijdens een failoververrichting, kan er een profielschakelaar zijn. Als een fout tijdens de download van één van playlist segmenten voorkomt, worden de controleparameters ABR zoals min/max toegestaan beetjetarief genegeerd.

