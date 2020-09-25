---
title: Bootstrap API
description: null
translation-type: tm+mt
source-git-commit: aa43834fea161c537c448b7616c9bd8f779d1a74
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Bootstrap API {#bootstrap-api}

Vereiste parametersGenereer een bootstrap

## Parameterbeschrijving {#parameter-description}

| parameter | beschrijving | formaten |
|---|---|---|
| pabimode | Hiermee schakelt u [gedeeltelijke invoeging](ad-insertion-live-linear-stream.md#partial-ad-break-support) en onderbreking in Live streams in. Mogelijke waarden:true om uit te schakelen (standaard uitgeschakeld) | HLS/DASH |
| ptadwindow | Duur (in seconden) van het terugzoek- en beslissingsvenster — hoe ver de Ad Insertion van Primetime terug naar ad-cues zoekt wanneer een DVR-gebruiker zich bij de stream aanmeldt. Een waarde van nul zal middenrol en besluitvorming in aanvankelijke manifest onbruikbaar maken, met besluit die slechts na de eerste update hervat. Deze parameter is nuttig om het toevoegen van toevoegingen aan zittingen onbruikbaar te maken die slechts een paar seconden kunnen duren (alias kanaalomdraaiend). Mogelijke waarden:numerieke tekenreeks 0-1800 (standaard 1800) | Alleen HLS |
| ptassetid | De unieke id van de inhoud die door de uitgever wordt toegewezen en onderhouden.  Vereist in combinatie met de Akamai Ad Scaler. | HLS/DASH |
| ptcdn | Lijst van één of meerdere CDNs aan gastheer transcoded activa. Zie Ondersteuning voor [meerdere CDN&#39;s voor](multi-cdn-support.md)meer informatie. Mogelijke waarden: akamai, level3, llnw (lichte netwerken), comcastBy gebrek, worden Primetime Ad Insertion CDNs gebruikt | HLS/DASH |
| ptcueformat | De opgegeven indeling van tags die moeten worden uitgevoerd en bepaald (bijvoorbeeld scte35). Mogelijke waarden: dpisimple, dpiscte35, element For custom cue formats, neem contact op met uw technische accountvertegenwoordiger voor de waarde die u voor uw gebruiksgeval wilt gebruiken | HLS/DASH |
| ptfailover | Signaleert de manifestserver om primaire en failover stromen te identificeren die in master playlist worden gespecificeerd, en hen te behandelen als gescheiden reeksen. Dit vergemakkelijkt failover en voorkomt timingsfouten. (Alleen voor Apple HLS-apparaten.) Voor meer informatie, zie [het Faciliteren van de speleromschakeling van HLS](hls-switching-to-failover.md) | Alleen HLS |
| ptmulticall | Indien ingeschakeld, wordt een afzonderlijke advertentieaanvraag gedaan voor elke in een VOD-element gevonden bron.  Standaard zal Primetime Ad Insertion proberen alle beschikbare informatie te verzamelen en deze in één aanvraag naar de advertentieserver te verzenden. Mogelijke waarden:true om uit te schakelen (standaard uitgeschakeld) | HLS/DASH |
| pttagds | Hiermee wordt injectie van EXT-X-DISCONTINUITY-SEQUENCE-tags in HLS-headers ingeschakeld.Mogelijke waarden:true om uit te schakelen (standaard uitgeschakeld) | Alleen HLS |
| pttimeline | Een tekenreeks met de gewenste tijdlijn voor plaatsing en inhoud van de advertentie, die de inhoudsstroom overschrijft en afbreekt. [ Zie VOD-tijdlijnindeling ] | HLS/DASH |
| pttoken | Hiermee schakelt u tokenbeveiligingsschema&#39;s voor inhoudsfragmenten/segmentautorisatie in voor CDN&#39;s Mogelijke waarden: akamai, lnw (licht), ctl (centurylink) (standaardtokenisatie is uitgeschakeld) | HLS/DASH |
| trackingmodus | Schema&#39;s voor het bijhouden van advertenties inschakelen:Mogelijke waarden:eenvoudig voor client-side- en trackingstreeksen voor server-side en eenvoudige tekstspatiëring voor hybride client/server en letterspatiëring (standaard wordt geen advertentie-tracking uitgevoerd) | HLS/DASH |
| trackingversie |  |  |
| ptadtimeout (zoals in 20.9.2) |  |  |
| ptparallelstream (zoals in 20.9.3) |  |  |
