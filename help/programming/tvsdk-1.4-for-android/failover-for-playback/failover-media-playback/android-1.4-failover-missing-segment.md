---
description: Wanneer een segment mist, bijvoorbeeld wanneer een bepaald segment er niet in slaagt te downloaden, probeert om door een verscheidenheid van failoverpogingen terug te krijgen. Als het niet kan herstellen, geeft het een fout uit.
title: Ontbrekende segment-failover
exl-id: e941008a-99a5-4fff-ac88-133abcf9380d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Ontbrekende segment-failover{#missing-segment-failover}

Wanneer een segment mist, bijvoorbeeld wanneer een bepaald segment er niet in slaagt te downloaden, probeert om door een verscheidenheid van failoverpogingen terug te krijgen. Als het niet kan herstellen, geeft het een fout uit.

Als een segment ontbreekt op de server omdat, bijvoorbeeld, het manifestdossier niet aanwezig is, kan het segment niet worden gedownload, etc., probeert TVSDK om over te ontbreken door de volgende opties te proberen:

1. Poging tot failover aan het zelfde segment, aan de zelfde beetjetarief, in een variantdossier.
1. Schakel over naar een andere bitsnelheid (ABR-switch) in hetzelfde bestand.
1. Doorloop elke beschikbare bitsnelheid in elke beschikbare variant.
1. Sla het segment over en geef een waarschuwing weer.

Wanneer TVSDK geen alternatief segment kan verkrijgen, wordt een `CONTENT_ERROR` foutmelding. Deze melding bevat een binnenbericht met de code `DOWNLOAD_ERROR` code. Als de stream met het probleem een alternatieve audiotrack is, wordt de `AUDIO_TRACK_ERROR` foutmelding.

Als de video-engine continu geen segmenten kan ophalen, beperkt deze de doorlopende segmentoverslaan tot 5, waarna het afspelen wordt gestopt en een `NATIVE_ERROR` met code 5.

>[!NOTE]
>
>De adaptieve parameters van de beetjetarief (ABR) worden niet in overweging genomen wanneer een failover voorkomt. Dit komt doordat het failover-mechanisme is ontworpen om een van de momenteel beschikbare afspeellijsten, ongeacht hun bitsnelheidprofiel, te gebruiken als back-upstreams.
>
>Tijdens een failoververrichting, kan er een profielschakelaar zijn. Als een fout tijdens de download van één van playlist segmenten voorkomt, worden de controleparameters ABR zoals min/max toegestaan beetjetarief genegeerd.
