---
description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
keywords: zero length ad;empty ad
seo-description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
seo-title: Extra fallback voor VAST- en VMAP-advertenties
title: Extra fallback voor VAST- en VMAP-advertenties
uuid: ecfeff31-b723-4a0d-99f2-48705a37b5f0
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Overzicht {#ad-fallback-for-vast-and-vmap-ads-overview}

Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

In de VAST/Digital Video Multiple Ad Playlist (VMAP)-specificatie staat dat voor advertenties waarvoor VAST-fallback is ingeschakeld, lege advertenties automatisch het gebruik van fallback-advertenties activeren. Als een VAST-advertentie leeg is, zoekt TVSDK naar een geldige vervanging van het HLS-mediatype in de fallback-advertenties. Als een VAST-advertentie in een omslag een ongeldig mediatype heeft, behandelt TVSDK deze advertentie als leeg. U kunt configureren of TVSDK hetzelfde moet doen voor inline-advertenties in een VMAP. Zie [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast) voor meer informatie over de functie VAST `fallbackOnNoAd`.

>[!NOTE]
>
>**Nullengteadvertenties**  - Als TVSDK een VAST antwoord aantreft dat een advertentie met een duur nul of een ad-einde zonder advertenties bevat, worden de gebeurtenissen AD_BREAK_START / AD_BREAK_COMPLETE geactiveerd voor die nullengte en einden. *Dit gedrag is alleen van toepassing op VOD-streams.* Deze gebeurtenissen worden door TVSDK geactiveerd, zelfs als uw app het SKIP-advertentiebeleid gebruikt.
>
>TVSDK voert *geen* brand AD_BREAK_START / AD_BREAK_COMPLETE gebeurtenissen uit voor Live streams, of wanneer een gebruiker gebruikmaakt van trucs of probeert voorbij de nullengte advertentie te gaan.

