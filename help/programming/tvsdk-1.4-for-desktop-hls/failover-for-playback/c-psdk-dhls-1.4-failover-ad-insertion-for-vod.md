---
description: Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet TVSDK een externe traceringsserver op de hoogte stellen van de voortgang van het afspelen van elke advertentie. Wanneer zich onverwachte situaties voordoen, neemt de Commissie passende maatregelen.
seo-description: Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet TVSDK een externe traceringsserver op de hoogte stellen van de voortgang van het afspelen van elke advertentie. Wanneer zich onverwachte situaties voordoen, neemt de Commissie passende maatregelen.
seo-title: Toevoeging en overname van advertenties voor VOD
title: Toevoeging en overname van advertenties voor VOD
uuid: 98505f63-ac43-4ff5-9f7b-895b6135df47
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Toevoeging en overname van advertenties voor VOD{#advertising-insertion-and-failover-for-vod}

Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet TVSDK een externe traceringsserver op de hoogte stellen van de voortgang van het afspelen van elke advertentie. Wanneer zich onverwachte situaties voordoen, neemt de Commissie passende maatregelen.

## Adverteringsfase {#section_0D45C6094D724B55868B48F9A3557A8B}

TVSDK neemt contact op met een advertentieservice, zoals Adobe Primetime en besluitvorming, en probeert het primaire afspeellijstbestand te verkrijgen dat overeenkomt met de videostream voor de advertentie. Tijdens de ad-resolving fase, doet TVSDK een vraag van HTTP aan de verre ad-leveringsserver en ontleedt de reactie van de server.

TVSDK ondersteunt de volgende typen advertentieproviders:

* Metagegevens en provider

   De advertentiegegevens worden gecodeerd in JSON-bestanden zonder opmaak.
* Primetime en beslissings- en provider

   TVSDK verzendt een verzoek, met inbegrip van een reeks richtingsparameters en een activa-identificatienummer, naar de Primetime en beslissingsbackend server. Primetime en besluitvorming reageren op een SMIL-document (synchronized multimedia integration language) dat de vereiste advertentietekst bevat.

Één van de volgende failoversituaties kan tijdens deze fase voorkomen:

* De gegevens kunnen niet worden teruggewonnen om redenen zoals een gebrek aan connectiviteit of een server-zijfout, zoals een middel kan niet worden gevonden etc.
* De gegevens zijn opgehaald, maar de indeling is ongeldig.

   Dit kan gebeuren omdat, bijvoorbeeld, het ontleden van de binnenkomende gegevens ontbrak.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.

## Ad-invoegfase {#section_1B18E8B5768B4873B3346294175B7340}

TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn in die overeenkomt met de hoofdinhoud.

Wanneer de ad-resolving fase volledig is, heeft TVSDK een geordende lijst van ad middelen die in ad-einden worden gegroepeerd. Elk ad-einde wordt op de tijdlijn van de hoofdinhoud geplaatst met behulp van een beginwaarde die in milliseconden (ms) wordt uitgedrukt. Elke advertentie in een advertentie-einde heeft een eigenschap duration die ook wordt uitgedrukt in ms. De advertenties in een pauze zijn stuk voor stuk aan elkaar gekoppeld. Als gevolg hiervan is de duur van een ad-break gelijk aan de som van de tijdsduur van de afzonderlijke samenstellende advertenties.

Failover kan in deze fase optreden met conflicten die tijdens het invoegen op de tijdlijn kunnen optreden. Voor specifieke combinaties van beginwaarden/duurwaarden voor begintijd en eindtijd van advertentie kunnen ad-valesegmenten elkaar overlappen. De overlapping treedt op wanneer het laatste gedeelte van een advertentie-einde het begin van de eerste advertentie in de volgende advertentie-einde snijdt. In deze situaties, verwerpt het recentere en onderbreking en vervolgt het ad-toevoegingsproces met het volgende punt op de lijst tot alle ad-onderbreking worden opgenomen of worden verworpen.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.

## Ad-playbackfase {#section_64777BD2CDA84EACB0A4EA6D68367CF5}

TVSDK downloadt de advertentiesegmenten en rendert deze op het scherm van het apparaat.

Op dit moment heeft TVSDK advertenties opgelost, op de tijdlijn geplaatst en geprobeerd de inhoud op het scherm weer te geven.

De volgende hoofdklassen van fouten kunnen in deze fase voorkomen:

* Fouten bij het verbinden met de hostserver
* Fouten bij het downloaden van het manifestbestand
* Fouten bij het downloaden van de mediasegmenten

Voor alle drie foutklassen heeft TVSDK gebeurtenissen doorgestuurd naar uw toepassing, waaronder:

* Gebeurtenissen van het bericht teweeggebracht wanneer een failover gebeurt.
* Gebeurtenissen van het bericht wanneer het profiel wegens het failoveralgoritme wordt veranderd.
* Gebeurtenissen van het bericht teweeggebracht wanneer alle failover opties zijn overwogen, en geen extra actie kan automatisch worden ondernomen.

   Uw toepassing moet de juiste actie ondernemen.

Of fouten voorkomen of niet, roept TVSDK `AdBreakPlaybackEvent.AD_BREAK_COMPLETE` voor elk `AdBreakPlaybackEvent.AD_BREAK_STARTED` en `AdPlaybackEvent.AD_COMPLETED` voor elk `AdPLaybackEvent.AD_STARTED`. Als segmenten echter niet kunnen worden gedownload, bevat de tijdlijn mogelijk tussenruimten. Wanneer de tussenruimten groot genoeg zijn, kunnen de waarden in de positie van de afspeelkop en de gerapporteerde en de voortgang discontinuïteit vertonen.
