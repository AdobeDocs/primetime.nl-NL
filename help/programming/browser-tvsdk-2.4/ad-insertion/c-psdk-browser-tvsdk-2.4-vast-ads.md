---
description: Wanneer Browser TVSDK om een advertentie vraagt die zich niet op uw primaire advertentieserver bevindt, moet de speler de advertentie aanvragen bij de secundaire server. De video Ad Serving Malplaatje (VAST) plaatst de norm van mededeling tussen advertentieservers en videospelers en is de reactie die door de secundaire advertentieserver wordt verzonden wanneer de advertentie wordt gevraagd.
seo-description: Wanneer Browser TVSDK om een advertentie vraagt die zich niet op uw primaire advertentieserver bevindt, moet de speler de advertentie aanvragen bij de secundaire server. De video Ad Serving Malplaatje (VAST) plaatst de norm van mededeling tussen advertentieservers en videospelers en is de reactie die door de secundaire advertentieserver wordt verzonden wanneer de advertentie wordt gevraagd.
seo-title: VAST-advertenties
title: VAST-advertenties
uuid: 052dae0c-2425-456c-aebe-531f68bb5aa8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# VAST-advertenties {#vast-ads}

Wanneer Browser TVSDK om een advertentie vraagt die zich niet op uw primaire advertentieserver bevindt, moet de speler de advertentie aanvragen bij de secundaire server. De video Ad Serving Malplaatje (VAST) plaatst de norm van mededeling tussen advertentieservers en videospelers en is de reactie die door de secundaire advertentieserver wordt verzonden wanneer de advertentie wordt gevraagd.

Voor meer informatie over VAST, zie [Digitale Video Ad Serving Template (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

Browser TVSDK steunt de volgende VAST en elementen:

## Wrapper- en inlineadvertenties {#section_11B8A1A8F52F4F77981C6AAC02185087}

De volgende elementen worden ondersteund:

* **`wrapper`** Wanneer de speler een secundaire advertentieserver moet contacteren om een advertentie aan te vragen, verstrekt het omslag element de omleidingsinformatie. Één omslagelement kan aan verscheidene omslagen richten die uiteindelijk aan een VAST advertentie richten.

* **`inline`** De volgende vereiste elementen worden ondersteund:

* `AdSystem`
* `AdTitle`
* `Impression`

   De volgende optionele elementen worden ondersteund:

* `Description`
* `Survey`
* `Error`

## Creatieve {#section_0121F948CB074E49A8132D202786CAA4}

Dit element is een bestand dat deel uitmaakt van een VAST-advertentie en een `creative` element bevat dat een lineaire advertentie, een niet-lineaire advertentie of een bijbehorende advertentie kan ondersteunen. In het `creative` element worden de elementen `id`, `sequence`en `adId` ondersteund.

Hier volgt meer informatie over de advertentietypen:

* **Lineaire advertenties** De volgende elementen worden ondersteund:

   * `TrackingEvent`, die het `Tracking` element bevat.
      * `Duration`
      * `AdParameters`
      * `VideoClicks`, met inbegrip van:

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`
         [!TIP]
In dit element worden de kenmerken `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework`, en `type` ondersteund.

* **Niet-lineaire advertenties** De volgende elementen worden ondersteund:

   * `Non-linear`
      [!TIP]
In dit element worden de kenmerken `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio`, en `minSuggestedDuration` ondersteund.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Extra advertenties** De volgende elementen worden ondersteund:

   * `Companion`
      [!TIP]
In dit element worden de `id`, `width`, `height`, `apiFramework`, `expandedWidth`, en `expandedHeight` attributen gesteund.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Extensies {#section_17401C75F419453BAE83637EEB6E1E60}

[!TIP]
Alleen Auditegerichte extensies worden ondersteund.

* `Extension`