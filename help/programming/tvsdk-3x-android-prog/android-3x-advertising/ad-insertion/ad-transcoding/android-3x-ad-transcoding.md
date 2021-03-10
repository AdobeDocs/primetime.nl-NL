---
description: Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video's.
title: Niet-compatibele advertenties opnieuw verpakken met gebruik van de Adobe Creative Repackaging Service (CRS)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Niet-compatibele advertenties opnieuw verpakken met gebruik van de Adobe Creative Repackaging Service (CRS) {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

Sommige advertenties van derden (of creatieve objecten) kunnen niet in de HLS-inhoudsstroom (HTTP Live Streaming) worden geplaatst omdat hun video-indeling niet compatibel is met HLS. Primetime en invoeging en TVSDK kunnen desgewenst proberen incompatibele advertenties om te zetten in compatibele M3U8-video&#39;s.

Advertenties die door verschillende derden worden aangeboden, zoals een bureau en server, uw inventarispartner of een advertentienetwerk, worden vaak in incompatibele indelingen geleverd, zoals de progressieve MP4-indeling voor downloaden.

Wanneer TVSDK voor het eerst een niet-compatibele advertentie tegenkomt, negeert de speler de advertentie en geeft een verzoek aan de creatieve herverpakkingsdienst (CRS) uit, die deel van Primetime en toevoegend achtereind uitmaakt, om de advertentie in een compatibel formaat te herverpakken. CRS probeert om veelvoudige vertoningen van de beetjetarief M3U8 van de advertentie te produceren en deze vertoningen op het Netwerk van de Levering van de Inhoud Primetime (CDN) op te slaan. De volgende keer dat TVSDK een advertentierespons ontvangt die naar die advertentie wijst, gebruikt de speler de HLS-compatibele M3U8-versie van de CDN.

Neem contact op met uw Adobe als u deze optionele CRS-functie wilt activeren.

>[!NOTE]
>
>Voor klanten van versie 3.0 van CRS (en vroeger), die met Versie 3.1 beginnen van CRS hebben de volgende veranderingen zowel veiligheid als prestaties verbeterd:
>
>* CRS 3.1 gaat verder met `https:` als de inhoud die wordt herverpakt `https:` gebruikt. Hierdoor wordt het potentieel van sommige spelers om onveilige inhoud te presenteren, beperkt.
   >
   >
* CRS 3.1 minimaliseert zeer netwerkvraag, verbeterend videostarttijd.

>



## CRS inschakelen in TVSDK-toepassingen {#enable-crs-in-tvsdk-applications}

Als u CRS wilt inschakelen in uw TVSDK-toepassingen, moet u de volgende informatie instellen in de instellingen voor de accountantscontrole:

1. CRS inschakelen in `AuditudeSettings`.

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
