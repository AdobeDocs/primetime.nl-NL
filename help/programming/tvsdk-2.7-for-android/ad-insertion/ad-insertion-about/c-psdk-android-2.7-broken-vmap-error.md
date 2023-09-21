---
description: Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).
keywords: 1109;NETWORK_AD_URL_FAILED;verbroken VMAP
title: Clientfoutafhandeling voor verbroken VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Clientfoutafhandeling voor verbroken VMAP {#client-error-handling-for-broken-vmap}

Wanneer TVSDK een gebroken VMAP in een reactie van de advertentieserver aantreft, verzendt het een fout 1109 (NETWORK_AD_URL_FAILED).

Afhankelijk van de aard van de reactie van de advertentieserver en van uw instellingen voor het laden van de advertentie, kan uw speler verschillende aantallen van 1109 fouten ontvangen wanneer TVSDK een verbroken VMAP aantreft in een reactie van de advertentieserver.

Laten wij een scenario overwegen waarin de reactie van de advertentieserver aan VMAP XML richt. Laat ons ook zeggen dat de reactie van de advertentieserver vier beschikbare ad groeven heeft, die elk aan zelfde VMAP richt. Tot slot, laten we zeggen dat deze VMAP gebroken is.

In dit scenario geldt dat als luie en het oplossen is ingeschakeld ( [Lozy en oplossen inschakelen](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)) verzendt TVSDK twee 1109 fouten (niet één zoals wordt verwacht): er wordt één fout verzonden bij elke parseringscontrole over de tijdlijn. Dit komt doordat TVSDK de advertenties in twee stappen parseert wanneer luie en het oplossen is ingeschakeld: de eerste controle vindt plaats vlak voordat het afspelen van de inhoud begint voor pre-roladvertenties en de tweede controle plaatsvindt nadat het afspelen is gestart, voor mid-roll en post-roll advertenties.

>[!NOTE]
>
>In dit scenario voert TVSDK slechts één fout van 1109 (slechts één parseringspas) uit als u luie bewerkingen uitschakelt en oplost.
