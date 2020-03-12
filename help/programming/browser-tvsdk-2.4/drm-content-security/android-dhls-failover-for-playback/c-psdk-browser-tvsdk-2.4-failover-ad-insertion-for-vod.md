---
description: Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet Browser-TVSDK een externe trackingserver informeren over de voortgang van het afspelen van elke advertentie. Wanneer zich onverwachte situaties voordoen, neemt de Commissie passende maatregelen.
seo-description: Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet Browser-TVSDK een externe trackingserver informeren over de voortgang van het afspelen van elke advertentie. Wanneer zich onverwachte situaties voordoen, neemt de Commissie passende maatregelen.
seo-title: Toevoeging en overname van advertenties voor VOD
title: Toevoeging en overname van advertenties voor VOD
uuid: 33f7aad5-fc4f-459d-8c29-01ba1353dfcc
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Toevoeging en overname van advertenties voor VOD{#advertising-insertion-and-failover-for-vod}

Het ad-invoegproces (VOD, Video on-demand) bestaat uit de fasen voor het omzetten, invoegen en toevoegen van de advertentie. Voor het bijhouden van advertenties moet Browser-TVSDK een externe trackingserver informeren over de voortgang van het afspelen van elke advertentie. Wanneer zich onverwachte situaties voordoen, neemt de Commissie passende maatregelen.

## Adverteringsfase {#section_F562CD6D0EF04AA9A0A3C0176A4EC340}

Browser TVSDK neemt contact op met een advertentieservice, zoals Adobe Primetime en besluitvorming, en probeert het primaire afspeellijstbestand te verkrijgen dat overeenkomt met de videostream voor de advertentie. Tijdens de ad-resolving fase, brengt Browser TVSDK een vraag van HTTP aan de verre ad-leveringsserver en ontleedt de reactie van de server.

Browser TVSDK ondersteunt de volgende typen advertentieproviders:

* Metagegevens en provider

   De advertentiegegevens worden gecodeerd in JSON-bestanden zonder opmaak.
* Adobe Primetime en beslissings- en provider

   Browser TVSDK verzendt een verzoek, met inbegrip van een reeks richtingsparameters en een element identificatienummer, naar de Adobe Primetime en beslissingsbackend server. Adobe Primetime en besluitvorming reageren op een SMIL-document (synchronized multimedia integration language) dat de vereiste advertentietekst bevat.

   Één van de volgende failoversituaties kan tijdens deze fase voorkomen:

   * De gegevens kunnen niet worden teruggewonnen om redenen zoals een gebrek aan connectiviteit of een server-zijfout, zoals een middel kan niet worden gevonden etc.
   * De gegevens zijn opgehaald, maar de indeling is ongeldig.

      Dit kan gebeuren omdat, bijvoorbeeld, het ontleden van de binnenkomende gegevens ontbrak.
   Browser TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.

## Ad-invoegfase {#section_88A0E4FA12394717A9D85689BD11D59F}

Browser-TVSDK voegt de alternatieve inhoud (advertenties) in de tijdlijn die overeenkomt met de hoofdinhoud.

Wanneer de ad-resolving fase volledig is, heeft Browser TVSDK een geordende lijst van ad middelen die in ad-einden worden gegroepeerd. Elk ad-einde wordt op de tijdlijn van de hoofdinhoud geplaatst met behulp van een beginwaarde die in milliseconden (ms) wordt uitgedrukt. Elke advertentie in een advertentie-einde heeft een eigenschap duration die ook wordt uitgedrukt in ms. De advertenties in een pauze zijn stuk voor stuk aan elkaar gekoppeld. Als gevolg hiervan is de duur van een ad-break gelijk aan de som van de tijdsduur van de afzonderlijke samenstellende advertenties.

Failover kan in deze fase optreden met conflicten die tijdens het invoegen op de tijdlijn kunnen optreden. Voor specifieke combinaties van beginwaarden/duurwaarden voor begintijd en eindtijd van advertentie kunnen ad-valesegmenten elkaar overlappen. De overlapping treedt op wanneer het laatste gedeelte van een advertentie-einde het begin van de eerste advertentie in de volgende advertentie-einde snijdt. In deze situaties verwijdert Browser-TVSDK het latere ad-invoegproces en gaat het ad-invoegproces verder met het volgende item in de lijst totdat alle ad-invoegingen zijn ingevoegd of verwijderd.

Browser TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.

## Ad-playbackfase {#section_7B0073BE9A744C74929263182C1243FC}

Browser-TVSDK downloadt de advertentiesegmenten en rendert deze op het scherm van het apparaat.

Op dit moment heeft Browser-TVSDK advertenties opgelost, ze op de tijdlijn geplaatst en probeert de inhoud op het scherm te renderen.

De volgende hoofdklassen van fouten kunnen in deze fase voorkomen:

* Fouten bij het verbinden met de hostserver
* Fouten bij het downloaden van het manifestbestand
* Fouten bij het downloaden van de mediasegmenten

Voor alle drie foutklassen heeft Browser TVSDK gebeurtenissen doorgestuurd naar uw toepassing, waaronder:

* Gebeurtenissen van het bericht teweeggebracht wanneer een failover gebeurt.
* Gebeurtenissen van het bericht wanneer het profiel wegens het failoveralgoritme wordt veranderd.
* Gebeurtenissen van het bericht teweeggebracht wanneer alle failover opties zijn overwogen, en geen extra actie kan automatisch worden ondernomen.

   Uw toepassing moet de juiste actie ondernemen.

Of er fouten optreden of niet, Browser-TVSDK geeft een melding wanneer een advertentie-einde begint en wanneer het is voltooid. Als segmenten echter niet kunnen worden gedownload, bevat de tijdlijn mogelijk tussenruimten. Wanneer de tussenruimten groot genoeg zijn, kunnen de waarden in de positie van de afspeelkop en de gerapporteerde en de voortgang discontinuïteit vertonen.
