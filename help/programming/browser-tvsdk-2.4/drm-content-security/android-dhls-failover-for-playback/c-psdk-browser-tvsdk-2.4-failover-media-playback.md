---
description: Voor live en VOD media, begint Browser TVSDK playback door playlist te downloaden die met het middenresolutie beetjetarief wordt geassocieerd en dan segmenten van de middenresolutie beetjetarief media te downloaden die door playlist wordt bepaald.
seo-description: Voor live en VOD media, begint Browser TVSDK playback door playlist te downloaden die met het middenresolutie beetjetarief wordt geassocieerd en dan segmenten van de middenresolutie beetjetarief media te downloaden die door playlist wordt bepaald.
seo-title: Afspelen van media
title: Afspelen van media
uuid: 454f84fe-8077-4f37-8e62-1d6ba0fcde27
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# Afspelen van media {#media-playback}

Voor live en VOD media, begint Browser TVSDK playback door playlist te downloaden die met het middenresolutie beetjetarief wordt geassocieerd en dan segmenten van de middenresolutie beetjetarief media te downloaden die door playlist wordt bepaald.

Browser TVSDK selecteert snel de afspeellijst met hoge bitsnelheid en de bijbehorende media en gaat door met het downloaden.

## failover van afspeellijst {#section_81A5822C108449E1A0E94A6E25DE9E8E} ontbreekt

Wanneer een volledige afspeellijst ontbreekt, bijvoorbeeld, wanneer het M3U8-bestand dat in een manifestbestand op hoofdniveau is opgegeven niet wordt gedownload, probeert Browser-TVSDK te herstellen. Als deze niet kan worden hersteld, bepaalt uw toepassing de volgende stap.

Als de afspeellijst die is gekoppeld aan de bitsnelheid met middelste resolutie ontbreekt, zoekt Browser-TVSDK naar een andere afspeellijst met dezelfde resolutie. Als dezelfde resolutie wordt gevonden, worden de afspeellijst van de variant en de segmenten vanaf de overeenkomende positie gedownload. Als Browser TVSDK niet de zelfde resolutie playlist vindt, zal het proberen door andere bitrate playlists en hun varianten te doorlopen. Een onmiddellijk lagere bitsnelheid is de eerste keuze, daarna de variant, enzovoort. Als alle onderste afspeellijsten met bitsnelheden en de bijbehorende varianten zijn uitgeput in de poging om een geldige afspeellijst te vinden, gaat Browser TVSDK naar de bovenste bitsnelheid en telt deze vanaf daar omlaag. Als er geen geldige afspeellijst kan worden gevonden, mislukt het proces en gaat de speler naar de status ERROR.

Uw toepassing kan bepalen hoe deze situatie wordt afgehandeld. U kunt bijvoorbeeld de speleractiviteit sluiten en de gebruiker naar de catalogusactiviteit verwijzen. De gebeurtenis van belang is de status of de staat veranderde gebeurtenis, en de overeenkomstige callback is de op status veranderde methode. Hier volgt code waarmee wordt gecontroleerd of de interne status van de speler wordt gewijzigd in ERROR:

```js
case AdobePSDK.MediaPlayerStatus.ERROR:  
var errorDesc = event.metadata.getValue('DESCRIPTION'); 
console.log(errorDesc); 
break; 
```
