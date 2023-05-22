---
description: Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.
keywords: lengte nul en;lege advertentie
title: Extra fallback voor VAST- en VMAP-advertenties
exl-id: 5cabb5f6-b895-48bc-9c9e-b22dd47539bd
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Extra fallback voor VAST- en VMAP-advertenties {#ad-fallback-for-vast-and-vmap-ads}

Voor Digital Video Ad Serving Template (VAST)-advertenties (of creatieven) waarvoor de fallback-regel is ingeschakeld, behandelt TVSDK een advertentie met een ongeldig mediatype als een lege advertentie en probeert het alternatieve advertenties te gebruiken. U kunt bepaalde aspecten van fallback-gedrag configureren.

In de VAST/Digital Video Multiple Ad Playlist (VMAP)-specificatie staat dat voor advertenties waarvoor VAST-fallback is ingeschakeld, lege advertenties automatisch het gebruik van fallback-advertenties activeren. Als een VAST-advertentie leeg is, zoekt TVSDK naar een geldige vervanging van het HLS-mediatype in de fallback-advertenties. Als een VAST-advertentie in een omslag een ongeldig mediatype heeft, behandelt TVSDK deze advertentie als leeg. U kunt configureren of TVSDK hetzelfde moet doen voor inline-advertenties in een VMAP. Voor meer informatie over de VAST `fallbackOnNoAd` functie, zie [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**Extra&#39;s met nullengte** - Als TVSDK een VAST-reactie aantreft die een advertentie met een duur nul of een ad-einde zonder advertenties bevat, worden de gebeurtenissen AD_BREAK_START / AD_BREAK_COMPLETE geactiveerd voor die gebeurtenissen met een lengte van nul en einden. *Dit gedrag is alleen van toepassing op VOD-streams.* Deze gebeurtenissen worden door TVSDK geactiveerd, zelfs als uw app het SKIP-advertentiebeleid gebruikt.
>
>TVSDK doet dat *niet* brand AD_BREAK_START / AD_BREAK_COMPLETE gebeurtenissen voor Actieve stromen, of wanneer een gebruiker trucs gebruikt of probeert voorbij de nul-lengte advertentie te gaan.
