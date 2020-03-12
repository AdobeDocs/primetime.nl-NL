---
description: TVSDK neemt contact op met een advertentieservice, zoals Adobe Primetime en besluitvorming, en probeert het primaire afspeellijstbestand te verkrijgen dat overeenkomt met de videostream voor de advertentie. Tijdens de ad-resolving fase, doet TVSDK een vraag van HTTP aan de verre ad-leveringsserver en ontleedt de reactie van de server.
seo-description: TVSDK neemt contact op met een advertentieservice, zoals Adobe Primetime en besluitvorming, en probeert het primaire afspeellijstbestand te verkrijgen dat overeenkomt met de videostream voor de advertentie. Tijdens de ad-resolving fase, doet TVSDK een vraag van HTTP aan de verre ad-leveringsserver en ontleedt de reactie van de server.
seo-title: Adverteringsfase
title: Adverteringsfase
uuid: b3e62a57-7e62-4e4e-8fa6-0d416785db67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Adverteringsfase{#ad-resolving-phase}

TVSDK neemt contact op met een advertentieservice, zoals Adobe Primetime en besluitvorming, en probeert het primaire afspeellijstbestand te verkrijgen dat overeenkomt met de videostream voor de advertentie. Tijdens de ad-resolving fase, doet TVSDK een vraag van HTTP aan de verre ad-leveringsserver en ontleedt de reactie van de server.

TVSDK ondersteunt de volgende typen advertentieproviders:

* Metagegevens en provider

   De advertentiegegevens worden gecodeerd in JSON-bestanden zonder opmaak.
* Primetime en beslissings- en provider

   TVSDK verzendt een verzoek, met inbegrip van een reeks richtingsparameters en een activa-identificatienummer, naar de Primetime en beslissingsbackend server. Primetime en besluitvorming reageren op een SMIL-document (synchronized multimedia integration language) dat de vereiste advertentietekst bevat.
* Aangepaste provider van advertentiemarkeringen

   Hiermee wordt de situatie afgehandeld waarin advertenties vanaf de server in de stream worden gebrand. TVSDK voert de daadwerkelijke invoeging niet uit, maar moet de advertenties bijhouden die aan de serverzijde zijn ingevoegd. Deze provider stelt de advertentiemarkeringen in die TVSDK gebruikt om de advertentie te volgen.

Één van de volgende failoversituaties kan tijdens deze fase voorkomen:

* De gegevens kunnen niet worden teruggewonnen om redenen zoals een gebrek aan connectiviteit of een server-zijfout, zoals een middel kan niet worden gevonden etc.
* De gegevens zijn opgehaald, maar de indeling is ongeldig.

   Dit kan gebeuren omdat, bijvoorbeeld, het ontleden van de binnenkomende gegevens ontbrak.

TVSDK geeft een waarschuwingsbericht over de fout weer en gaat door met de verwerking.
