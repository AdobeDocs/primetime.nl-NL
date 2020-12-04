---
description: Voor live- en video-on-demand-media (VOD) begint TVSDK met het afspelen door de afspeellijst te downloaden die is gekoppeld aan de bitsnelheid met de middelste resolutie en worden de mediasegmenten gedownload die door die afspeellijst worden gedefinieerd. Deze selecteert snel de afspeellijst met hoge bitsnelheid en de bijbehorende media en gaat verder met het downloaden.
seo-description: Voor live- en video-on-demand-media (VOD) begint TVSDK met het afspelen door de afspeellijst te downloaden die is gekoppeld aan de bitsnelheid met de middelste resolutie en worden de mediasegmenten gedownload die door die afspeellijst worden gedefinieerd. Deze selecteert snel de afspeellijst met hoge bitsnelheid en de bijbehorende media en gaat verder met het downloaden.
seo-title: Afspelen van media en failover
title: Afspelen van media en failover
uuid: e0072eeb-8ad1-436f-bf4a-fee6885a25bd
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---


# Afspelen van media en failover {#media-playback-and-failover}

Voor live- en video-on-demand-media (VOD) begint TVSDK met het afspelen door de afspeellijst te downloaden die is gekoppeld aan de bitsnelheid met de middelste resolutie en worden de mediasegmenten gedownload die door die afspeellijst worden gedefinieerd. Deze selecteert snel de afspeellijst met hoge bitsnelheid en de bijbehorende media en gaat verder met het downloaden.

## failover van afspeellijst {#section_4EA0AEFA7FB84FCEA699DFB10B135368} ontbreekt

Wanneer een volledige afspeellijst ontbreekt, bijvoorbeeld, wanneer het M3U8-bestand dat is opgegeven in een manifestbestand op hoofdniveau niet wordt gedownload, probeert TVSDK te herstellen. Als deze niet kan worden hersteld, bepaalt uw toepassing de volgende stap.

Als de afspeellijst die is gekoppeld aan de bitsnelheid met middelste resolutie ontbreekt, zoekt TVSDK naar een andere afspeellijst met dezelfde resolutie. Als het de zelfde resolutie vindt, begint TVSDK de variantplaylist en de segmenten van de passende positie te downloaden. Als de speler niet dezelfde resolutie-afspeellijst vindt, probeert deze andere afspeellijsten met bitsnelheden en hun varianten te doorlopen. Een onmiddellijk lagere bitsnelheid is de eerste keuze, daarna de variant, enzovoort. Als alle onderste afspeellijsten met bitsnelheden en de bijbehorende varianten zijn uitgeput in de poging om een geldige afspeellijst te vinden, gaat TVSDK naar de bovenste bitsnelheid en wordt het aantal van daaruit verlaagd. Als er geen geldige afspeellijst kan worden gevonden, mislukt het proces en gaat de speler naar de status ERROR.

Uw toepassing kan bepalen hoe deze situatie wordt afgehandeld. U kunt bijvoorbeeld de speleractiviteit sluiten en de gebruiker naar de catalogusactiviteit verwijzen. De gebeurtenis van belang is de `STATUS_CHANGED` gebeurtenis, en de overeenkomstige callback is de `onStatusChanged` methode. Hier volgt code die controleert of de speler zijn interne status in `ERROR` verandert:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## Ontbrekende segmentfailover {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

Wanneer een segment ontbreekt, bijvoorbeeld wanneer een bepaald segment niet kan downloaden, probeert TVSDK om door een verscheidenheid van failoverpogingen terug te krijgen. Als het niet kan herstellen, geeft het een fout uit.

Als een segment ontbreekt op de server omdat, bijvoorbeeld, het manifestdossier niet aanwezig is, kan het segment niet worden gedownload, etc., probeert TVSDK om over te ontbreken door de volgende opties te proberen:

1. Poging tot failover aan het zelfde segment, aan de zelfde beetjetarief, in een variantdossier.
1. Schakel over naar een andere bitsnelheid (ABR-switch) in hetzelfde bestand.
1. Doorloop elke beschikbare bitsnelheid in elke beschikbare variant.
1. Sla het segment over en geef een waarschuwing weer.

Wanneer TVSDK geen alternatief segment kan verkrijgen, leidt het tot een `CONTENT_ERROR` foutenmelding. Deze melding bevat een binnenste melding met de code `DOWNLOAD_ERROR`. Als de stream met het probleem een alternatieve audiotrack is, genereert TVSDK de foutmelding `AUDIO_TRACK_ERROR`.

Als de video-engine continu geen segmenten kan ophalen, beperkt het continue segmentoverslaan tot 5, waarna het afspelen wordt gestopt en geeft TVSDK een `NATIVE_ERROR` met code 5 uit.

>[!NOTE]
>
>**Beperkingen**
>
>Hier volgen enkele beperkingen waarmee u rekening moet houden:
>
>* De adaptieve parameters van de beetjetarief (ABR) worden niet in overweging genomen wanneer een failover voorkomt.
>
>  
Dit komt doordat het failover-mechanisme is ontworpen om een van de momenteel beschikbare afspeellijsten, ongeacht hun bitsnelheidprofiel, te gebruiken als back-upstreams.
>* Tijdens een failoververrichting, kan er een profielschakelaar zijn.
>
>  
Als een fout tijdens de download van één van playlist segmenten voorkomt, worden de controleparameters ABR zoals min/max toegestaan beetjetarief genegeerd.
