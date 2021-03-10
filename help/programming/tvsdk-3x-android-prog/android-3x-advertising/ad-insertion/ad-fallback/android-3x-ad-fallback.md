---
description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
keywords: lengte nul en;lege advertentie
title: Extra fallback voor VAST- en VMAP-advertenties
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Extra fallback voor VAST- en VMAP-advertenties {#ad-fallback-for-vast-and-vmap-ads}

Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

In de VAST/Digital Video Multiple Ad Playlist (VMAP)-specificatie staat dat voor advertenties waarvoor VAST-fallback is ingeschakeld, lege advertenties automatisch het gebruik van fallback-advertenties activeren. Als een VAST-advertentie leeg is, zoekt TVSDK naar een geldige vervanging van het HLS-mediatype in de fallback-advertenties. Als een VAST-advertentie in een omslag een ongeldig mediatype heeft, behandelt TVSDK deze advertentie als leeg. U kunt configureren of TVSDK hetzelfde moet doen voor inline-advertenties in een VMAP. Zie [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast) voor meer informatie over de functie VAST `fallbackOnNoAd`.

>[!NOTE]
>
>**Nullengteadvertenties**  - Als TVSDK een VAST antwoord aantreft dat een advertentie met een duur nul of een ad-einde zonder advertenties bevat, worden de gebeurtenissen AD_BREAK_START / AD_BREAK_COMPLETE geactiveerd voor die nullengte en einden. *Dit gedrag is alleen van toepassing op VOD-streams.* Deze gebeurtenissen worden door TVSDK geactiveerd, zelfs als uw app het SKIP-advertentiebeleid gebruikt.
>
>TVSDK voert *geen* brand AD_BREAK_START / AD_BREAK_COMPLETE gebeurtenissen uit voor Live streams, of wanneer een gebruiker gebruikmaakt van trucs of probeert voorbij de nullengte advertentie te gaan.