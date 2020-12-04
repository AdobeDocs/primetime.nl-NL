---
description: Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet TVSDK een externe traceringsserver op de hoogte stellen van de voortgang van het afspelen van elke advertentie. In onverwachte situaties neemt TVSDK de juiste maatregelen.
seo-description: Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet TVSDK een externe traceringsserver op de hoogte stellen van de voortgang van het afspelen van elke advertentie. In onverwachte situaties neemt TVSDK de juiste maatregelen.
seo-title: Toevoeging en overname van advertenties voor VOD
title: Toevoeging en overname van advertenties voor VOD
uuid: 74cc35e6-6479-4572-a3b3-05ff6344272a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---


# Toevoeging en overname van advertenties voor VOD {#advertising-insertion-and-failover-for-vod}

Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet TVSDK een externe traceringsserver op de hoogte stellen van de voortgang van het afspelen van elke advertentie. In onverwachte situaties neemt TVSDK de juiste maatregelen.

## Adverterende fase {#section_5DD3A7DA79E946298BFF829A60202E1C}

TVSDK neemt contact op met een advertentieservice, zoals Adobe Primetime en besluitvorming, en probeert het primaire afspeellijstbestand te verkrijgen dat overeenkomt met de videostream voor de advertentie. Tijdens de ad-resolving fase, doet TVSDK een vraag van HTTP aan de verre ad-leveringsserver en ontleedt de reactie van de server.

TVSDK ondersteunt de volgende typen advertentieproviders:

* Metagegevens en provider

   De advertentiegegevens worden gecodeerd in JSON-bestanden zonder opmaak.
* Primetime en beslissings- en provider

   TVSDK verzendt een verzoek, met inbegrip van een reeks richtingsparameters en een activa-identificatienummer, naar de Primetime en beslissingsback-end server. Primetime en besluitvorming reageren op een SMIL-document (Synchronized Multimedia Integration Language) dat de vereiste advertentietails bevat.
* Aangepaste provider van advertentiemarkeringen

   Hiermee wordt de situatie afgehandeld waarin advertenties vanaf de server in de stream worden gebrand. TVSDK voert de daadwerkelijke invoeging niet uit, maar moet de advertenties bijhouden die aan de serverzijde zijn ingevoegd. Deze provider stelt de advertentiemarkeringen in die TVSDK gebruikt om de advertentie te volgen.

Één van de volgende failoversituaties kan tijdens deze fase voorkomen:

* De gegevens kunnen niet worden opgehaald omdat, bijvoorbeeld, het gebrek aan connectiviteit of een server-zijfout, zoals een middel niet kan worden gevonden, etc.
* De gegevens zijn opgehaald, maar de indeling is ongeldig.

   Dit kan gebeuren omdat, bijvoorbeeld, het ontleden van de binnenkomende gegevens ontbrak.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.

## Advertentiefase {#section_29F7F7756C8B40B99AD4C3DD16B72B5B}

TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.

Wanneer de ad-resolving fase volledig is, heeft TVSDK een geordende lijst van ad middelen die in ad-einden worden gegroepeerd. Elk ad-einde wordt op de tijdlijn van de hoofdinhoud geplaatst met een beginwaarde die in milliseconden (ms) wordt uitgedrukt. Elke advertentie in een advertentie-einde heeft een eigenschap duration die ook wordt uitgedrukt in ms. De advertenties in een ad-break zijn geketend, waardoor de duur van een ad-break gelijk is aan de som van de tijdsduur van de afzonderlijke samenstellende advertenties.

Failover kan in deze fase optreden met conflicten die tijdens het invoegen op de tijdlijn kunnen optreden. Voor specifieke combinaties van beginwaarden/duurwaarden voor begintijd en eindtijd van advertentie kunnen ad-valesegmenten elkaar overlappen. Deze overlapping treedt op wanneer het laatste gedeelte van een advertentie-einde het begin van de eerste advertentie in de volgende advertentie-einde snijdt. In deze situaties verwijdert TVSDK het latere ad-invoegproces en gaat het ad-invoegproces verder met het volgende item in de lijst totdat alle ad-invoegingen zijn ingevoegd of verwijderd.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.

## Ad-playbackfase {#section_DA816F88AF8A4A5A8FD0DE2D54A86031}

TVSDK downloadt de advertentiesegmenten en rendert deze op het scherm van het apparaat.

TVSDK heeft nu advertenties opgelost, de advertenties op de tijdlijn geplaatst en probeert de inhoud op het scherm weer te geven.

De volgende hoofdklassen van fouten kunnen tijdens de volgende fasen voorkomen:

* Bij verbinding maken met de hostserver.
* Tijdens het downloaden van het manifestbestand.
* Tijdens het downloaden van de mediasegmenten.

TVSDK stuurt de getriggerde gebeurtenissen door naar uw toepassing, inclusief meldingsgebeurtenissen die worden geactiveerd wanneer:

* Een failover gebeurt.
* Het profiel wordt gewijzigd als gevolg van het failover-algoritme.
* Alle failover opties zijn overwogen, en geen extra actie kan automatisch worden ondernomen.

   Uw toepassing moet de juiste actie ondernemen.

Ongeacht of er fouten optreden, roept TVSDK `onAdBreakComplete` aan voor elke `onAdBreakStart` en `onAdComplete` voor elke `onAdStart`. Als segmenten echter niet kunnen worden gedownload, bevat de tijdlijn mogelijk tussenruimten. Wanneer de tussenruimten groot genoeg zijn, kunnen de waarden in de positie van de afspeelkop en de gerapporteerde en de voortgang discontinuïteit vertonen.