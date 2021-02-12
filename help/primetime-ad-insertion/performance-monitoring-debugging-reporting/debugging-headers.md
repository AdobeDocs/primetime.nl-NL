---
title: Fouten opsporen in koppen
description: null
translation-type: tm+mt
source-git-commit: 45e5c8e6144adf4a405bde7d8d19505b7ad549e0
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# Foutopsporingskoppen (X-ADBE-AI-X1) {#debugging-headers}

SSAI verzendt de kopballen van HTTP die kunnen worden gebruikt om informatie te verzamelen en prestaties voor productiesessies te bepalen, die in X-ADBE-AI-X1 kopbal worden gevestigd.

Voorbeeldkoptekst:
`X-ADBE-AI-X1: 0 1 1594181097704 15126333-5ba9-49b8-a219-4f37e60d259c v 0 1 30 2 1 199 2 185 497 204 104 0 1 0 4`

De velden worden als volgt beschreven:

| Naam | Beschrijving | Voorbeeld |
|--- |--- |--- |
| isActivePreroll | Of een advertentieoproep voor de prullenbak is verzonden | 0 |
| isActiveMidroll | Of een ad call for midroll werd verzonden | 1 |
| Aanvraag-id | Interne SSAI | 1594181097704 |
| Sessie-id | Sessie-id van de aanvraag | 15126333-5ba9-49b8-a219-4f37e60d259c |
| Type stream | u=variant, l=live, v=vod | v |
| isBootstrap | Of dit verzoek een laarzentrekker is | 0 |
| Aantal extra einden | Totaal aantal en onderbrekingen in dit manifest | 1 |
| Totale duur van einde advertentie | Totale duur van ad-onderbreking, in seconden | 30 |
| Ad Calls Count | Aantal ad vraag die in dit verzoek wordt verzonden | 2 |
| Redirect Ad de Telling van Vraag | Aantal omleidings en vraag die in dit verzoek wordt verzonden | 3 |
| Totale duur van AdCall | Totale verwerkingstijd AdCall | 199 |
| Aantal ingevoegde advertenties | Aantal advertenties die in het manifest zijn ingevoegd | 2 |
| Tijdstip bronmanifest | Tijd besteed aan het ophalen van alleen inhoud | 185 |
| Totale tijd van aanvraag | Totale tijd die is besteed aan het ophalen van inhoud en advertenties | 497 |
| Fetch-tijd voor manifest toevoegen (totaal) | Totale hoeveelheid tijd voor het ophalen en manifesten | 204 |
| Geanifest fest fetch time (werkelijke) | Werkelijke hoeveelheid tijd voor het ophalen en tegelijkertijd manifesten | 104 |
| Cachetips voor inhoud | Aantal treffers voor inhoudscache | 0 |
| Inhoudcache-fout | Aantal ontbrekende inhoudcache | 1 |
| Cachehit voor manifest toevoegen | Aantal cachesultaten van advertentiemanifest | 0 |
| Onjuffrouw cache toevoegen | Aantal ontbrekende cache voor advertentiemanifest | 4 |