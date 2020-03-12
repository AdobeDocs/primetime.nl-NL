---
description: Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).
keywords: 1109;NETWORK_AD_URL_FAILED;broken VMAP
seo-description: Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).
seo-title: Clientfoutafhandeling voor verbroken VMAP
title: Clientfoutafhandeling voor verbroken VMAP
uuid: ab2c567d-d945-4ebe-b65a-c1f13518a576
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Clientfoutafhandeling voor verbroken VMAP {#client-error-handling-for-broken-vmap}

Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).

Afhankelijk van de aard van de reactie van de advertentieserver en van uw instellingen voor het laden van de advertentie, kan uw speler verschillende aantallen van 1109 fouten ontvangen wanneer TVSDK een verbroken VMAP aantreft in een reactie van de advertentieserver.

Laten wij een scenario overwegen waarin de reactie van de advertentieserver aan VMAP XML richt. Laat ons ook zeggen dat de reactie van de advertentieserver vier beschikbare ad groeven heeft, die elk aan zelfde VMAP richt. Tot slot, laten we zeggen dat deze VMAP gebroken is.

In dit scenario, als luie en het oplossen wordt toegelaten ([laat luie toe en het oplossen](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/t-enable-lazy-ad-resolving.md)), zal TVSDK twee 1109 fouten (niet zoals te verwachten) verzenden: er wordt één fout verzonden bij elke parseringscontrole over de tijdlijn. Dit komt doordat TVSDK de advertenties in 2 stappen parseert wanneer luie en resolutie is ingeschakeld: De eerste controle vindt plaats vlak voordat het afspelen van de inhoud begint voor pre-roll-advertenties. De tweede controle vindt plaats nadat het afspelen is gestart, voor mid-roll en post-roll-advertenties.

>[!NOTE]
>
>In dit scenario voert TVSDK slechts één fout van 1109 (slechts één parseringspas) uit als u luie bewerkingen uitschakelt en oplost.