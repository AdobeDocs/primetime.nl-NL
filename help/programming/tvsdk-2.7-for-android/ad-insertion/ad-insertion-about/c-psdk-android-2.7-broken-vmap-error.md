---
description: Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).
keywords: 1109;NETWORK_AD_URL_FAILED;verbroken VMAP
title: Clientfoutafhandeling voor verbroken VMAP
exl-id: 268307a9-b72e-45fa-84f2-a8e7d969e2ba
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Clientfoutafhandeling voor verbroken VMAP {#client-error-handling-for-broken-vmap}

Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).

Afhankelijk van de aard van de reactie van de advertentieserver en van uw instellingen voor het laden van de advertentie, kan uw speler verschillende aantallen van 1109 fouten ontvangen wanneer TVSDK een verbroken VMAP aantreft in een reactie van de advertentieserver.

Laten wij een scenario overwegen waarin de reactie van de advertentieserver aan VMAP XML richt. Laat ons ook zeggen dat de reactie van de advertentieserver vier beschikbare ad groeven heeft, die elk aan zelfde VMAP richt. Tot slot, laten we zeggen dat deze VMAP gebroken is.

In dit scenario geldt dat als luie en het oplossen is ingeschakeld ( [Lozy en oplossen inschakelen](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)), verzendt TVSDK twee 1109 fouten (niet één zoals wordt verwacht): er wordt één fout verzonden bij elke parseringscontrole over de tijdlijn. Dit komt doordat TVSDK de advertenties in 2 stappen parseert wanneer luie en resolutie is ingeschakeld: De eerste controle vindt plaats vlak voordat het afspelen van de inhoud begint voor pre-roll-advertenties. De tweede controle vindt plaats nadat het afspelen is gestart, voor mid-roll en post-roll-advertenties.

>[!NOTE]
>
>In dit scenario voert TVSDK slechts één fout van 1109 (slechts één parseringspas) uit als u luie bewerkingen uitschakelt en oplost.
