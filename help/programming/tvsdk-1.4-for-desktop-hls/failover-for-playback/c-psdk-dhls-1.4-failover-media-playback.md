---
description: Voor live en video-on-demand (VOD) media begint TVSDK met afspelen door de afspeellijst te downloaden die is gekoppeld aan de bitsnelheid met de middelste resolutie en worden de mediasegmenten gedownload die door die afspeellijst zijn gedefinieerd. Deze selecteert snel de afspeellijst met hoge bitsnelheid en de bijbehorende media en gaat verder met het downloaden.
title: Afspelen van media en failover
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---


# Afspelen van media en failover{#media-playback-and-failover}

Voor live en video-on-demand (VOD) media begint TVSDK met afspelen door de afspeellijst te downloaden die is gekoppeld aan de bitsnelheid met de middelste resolutie en worden de mediasegmenten gedownload die door die afspeellijst zijn gedefinieerd. Deze selecteert snel de afspeellijst met hoge bitsnelheid en de bijbehorende media en gaat verder met het downloaden.

## failover van afspeellijst {#section_E6B6A15930894F56A0A8501577B35E7F} ontbreekt

Wanneer een volledige afspeellijst ontbreekt, bijvoorbeeld wanneer het M3U8-bestand dat in een manifestbestand op hoofdniveau is opgegeven niet wordt gedownload, probeert TVSDK het bestand te herstellen. Als deze niet kan worden hersteld, bepaalt uw toepassing de volgende stap.

Als de afspeellijst die is gekoppeld aan de bitsnelheid met middelste resolutie ontbreekt, zoekt TVSDK naar een andere afspeellijst met dezelfde resolutie. Als dezelfde resolutie wordt gevonden, worden de afspeellijst van de variant en de segmenten vanaf de overeenkomende positie gedownload. Als TVSDK niet dezelfde afspeellijst met resolutie vindt, probeert het andere afspeellijsten met bitsnelheden en hun varianten te doorlopen. Een onmiddellijk lagere bitsnelheid is de eerste keuze, daarna de variant, enzovoort. Als alle onderste afspeellijsten met bitsnelheden en de bijbehorende varianten zijn uitgeput in de poging om een geldige afspeellijst te vinden, gaat TVSDK naar de bovenste bitsnelheid en wordt het aantal van daaruit verlaagd. Als er geen geldige afspeellijst kan worden gevonden, mislukt het proces en gaat de speler naar de status ERROR.

Uw toepassing kan bepalen hoe deze situatie wordt afgehandeld. U kunt bijvoorbeeld de speleractiviteit sluiten en de gebruiker naar de catalogusactiviteit verwijzen. De gebeurtenis van belang is de `STATUS_CHANGED` gebeurtenis, en de overeenkomstige callback is de `onStatusChange` methode. Hier volgt code waarmee wordt gecontroleerd of de interne status van de speler wordt gewijzigd in ERROR:

Zie het bestand `PSDKDemo` voor meer informatie. Gebeurtenislisteners zijn gekoppeld aan de MediaPlayer-instantie.

```
case MediaPlayerStatus.ERROR: 
Alert.show(event.error.toString(), “Error occurred”); 
break;
```

Als het netwerk aan de clientzijde uitvalt, kunt u deze code gebruiken om te verifiëren.

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

API zal url verstrekken die wordt gebruikt om te verifiëren als het cliënt zijnetwerk neer is. Dit zou een geldige url moeten zijn, die http antwoordcode 200 op HTTP- verzoeken terugkeert.

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

Als setNetworkDownVerificationUrl niet wordt geplaatst, gebruikt TVSDK de MainManifest url door gebrek om te bepalen als het netwerk neer is.

## Ontbrekende segmentfailover {#section_ED8CF666289042D39E9914D42BDD9BA4}

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
>De adaptieve parameters van de beetjetarief (ABR) worden niet in overweging genomen wanneer een failover voorkomt. Dit komt doordat het failover-mechanisme is ontworpen om een van de momenteel beschikbare afspeellijsten, ongeacht hun bitsnelheidprofiel, te gebruiken als back-upstreams.
>
>Tijdens een failoververrichting, kan er een profielschakelaar zijn. Als een fout tijdens de download van één van playlist segmenten voorkomt, worden de controleparameters ABR zoals min/max toegestaan beetjetarief genegeerd.

