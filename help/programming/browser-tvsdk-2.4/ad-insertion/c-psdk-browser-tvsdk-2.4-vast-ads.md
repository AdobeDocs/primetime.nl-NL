---
description: Wanneer Browser TVSDK om een advertentie vraagt die zich niet op uw primaire advertentieserver bevindt, moet de speler de advertentie aanvragen bij de secundaire server. De video Ad Serving Malplaatje (VAST) plaatst de norm van mededeling tussen advertentieservers en videospelers en is de reactie die door de secundaire advertentieserver wordt verzonden wanneer de advertentie wordt gevraagd.
title: VAST-advertenties
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# VAST advertenties {#vast-ads}

Wanneer Browser TVSDK om een advertentie vraagt die zich niet op uw primaire advertentieserver bevindt, moet de speler de advertentie aanvragen bij de secundaire server. De video Ad Serving Malplaatje (VAST) plaatst de norm van mededeling tussen advertentieservers en videospelers en is de reactie die door de secundaire advertentieserver wordt verzonden wanneer de advertentie wordt gevraagd.

Zie [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf) voor meer informatie over VAST.

Browser TVSDK steunt de volgende VAST en elementen:

## Wrapper- en inline-advertenties {#section_11B8A1A8F52F4F77981C6AAC02185087}

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

Dit element is een bestand dat een onderdeel is van een VAST-advertentie en een `creative`-element bevat dat een lineaire advertentie, een niet-lineaire advertentie of een bijbehorende advertentie kan ondersteunen. In het `creative` element, worden `id`, `sequence`, en `adId` elementen gesteund.

Hier volgt meer informatie over de advertentietypen:

* **Lineaire** advertentiesDe volgende elementen worden ondersteund:

   * `TrackingEvent`, die het  `Tracking` element bevat.
      * `Duration`
      * `AdParameters`
      * `VideoClicks`, met inbegrip van:

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`

         >[!TIP]
         >
         >In dit element worden de kenmerken `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework` en `type` ondersteund.

* **Niet-lineaire** advertentiesDe volgende elementen worden ondersteund:

   * `Non-linear`

      >[!TIP]
      >
      >In dit element worden de kenmerken `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio` en `minSuggestedDuration` ondersteund.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Companion** adsDe volgende elementen worden ondersteund:

   * `Companion`

      >[!TIP]
      >
      >In dit element worden de kenmerken `id`, `width`, `height`, `apiFramework`, `expandedWidth` en `expandedHeight` ondersteund.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Extensies {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Alleen Auditegerichte extensies worden ondersteund.

* `Extension`
