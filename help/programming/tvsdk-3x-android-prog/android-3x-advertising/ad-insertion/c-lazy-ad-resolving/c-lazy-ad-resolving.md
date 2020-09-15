---
description: Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functies Lazy Ad Loading en Lazy Ad Resolving kunt u deze opstartvertraging verminderen. Lazy Adv Resolving is significant veranderd in versie 3.0. In Lazy Ad die voorafgaand aan 3.0, en resolutie werd gebroken in twee stappen, die enkel pre-rollen advertenties vóór de VOORBEREIDENDE status oplossen, en midden rollen en post-rollen na de VOORBEREIDENDE status. Dit is gewijzigd en de afbrekingen van de advertentie worden nu opgelost met een opgegeven interval vóór de positie van het advertentierak.
keywords: Lazy;Ad resolving;Ad loading
seo-description: Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functies Lazy Ad Loading en Lazy Ad Resolving kunt u deze opstartvertraging verminderen. Lazy Adv Resolving is significant veranderd in versie 3.0. In Lazy Ad die voorafgaand aan 3.0, en resolutie werd gebroken in twee stappen, die enkel pre-rollen advertenties vóór de VOORBEREIDENDE status oplossen, en midden rollen en post-rollen na de VOORBEREIDENDE status. Dit is gewijzigd en de afbrekingen van de advertentie worden nu opgelost met een opgegeven interval vóór de positie van het advertentierak.
seo-title: Just-in-Time en oplossing
title: Just-in-Time en oplossing
uuid: 77028f6e-7e53-45d1-bcc0-54f8224d6d18
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# Overzicht {#just-in-time-ad-resolving-overview}

Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functies Lazy Ad Loading en Lazy Ad Resolving kunt u deze opstartvertraging verminderen. Lazy Adv Resolving is significant veranderd in versie 3.0. In Lazy Ad die voorafgaand aan 3.0, en resolutie werd gebroken in twee stappen, die enkel pre-rollen advertenties vóór de VOORBEREIDENDE status oplossen, en midden rollen en post-rollen na de VOORBEREIDENDE status. Dit is gewijzigd en de afbrekingen van de advertentie worden nu opgelost met een opgegeven interval vóór de positie van het advertentierak.

* Eenvoudig proces voor het oplossen en laden van bestanden:

   1. TVSDK downloadt een manifest (playlist) en *lost* alle advertenties op.
   1. TVSDK *laadt* alle advertenties en plaatst deze op de tijdlijn.
   1. TVSDK verplaatst de speler naar de status PREPARED en begint met afspelen van inhoud.

   De speler gebruikt de URL&#39;s in het manifest om de advertentie-inhoud (creatieven) te verkrijgen, zorgt ervoor dat de advertentie-inhoud een indeling heeft die TVSDK kan afspelen en dat TVSDK de advertenties op de tijdlijn plaatst. Dit basisproces voor het oplossen en laden van advertenties kan een onaanvaardbare lange wachttijd veroorzaken voor een gebruiker die wacht om zijn inhoud af te spelen, vooral als het manifest meerdere advertentie-URL&#39;s bevat.

* *Lazy advertentie laden*:

   1. TVSDK downloadt een afspeellijst en *lost* alle advertenties op.
   1. TVSDK *laadt* pre-roladvertenties, verplaatst de speler naar de status PREPARED en begint met het afspelen van inhoud.
   1. TVSDK *laadt* de resterende advertenties en plaatst deze op de tijdlijn wanneer het afspelen plaatsvindt.

   Met deze functie wordt het basisproces verbeterd doordat de speler in de status PREPARED wordt geplaatst voordat alle advertenties worden geladen.

* *Lazy en oplossen*:

   1. TVSDK downloadt de afspeellijst.
   1. TVSDK verhelpt alle pre-roll-advertenties en laadt deze, verplaatst de speler naar de status PREPARED en begint de inhoud af te spelen.
   1. TVSDK lost en elk van de resterende ad-einden individueel op basis van de volgende berekening op:

      `AdvertisingMetadata::getDelayAdLoadingTolerance() + PlayBufferTime::playBufferTime + the value defined in EXT-X-TARGETDURATION`

      Standaard is dit voor inhoud met een 6 seconden durende doelduur 5,0 + 30,0 + 6,0 seconden (41 seconden)

   1. Als een advertentieonderbreking binnen 10 seconden na de beginpositie voorkomt, zal het samen met pre-rol advertenties vóór de PREPARED status worden opgelost.

>[!IMPORTANT]
>
>**Factoren die in overweging moeten worden genomen met Lazy Ad Resolving:**
>
>* Lazy Ad Resolving wordt slechts gesteund voor stromen VOD met wijzen SERVER_MAP en MANIFEST_CUES.
>* Lazy Ad Resolving is niet standaard ingeschakeld. Als deze optie is uitgeschakeld, worden alle advertenties opgelost in VOD-streams voordat het afspelen wordt gestart.
>* Lazy Ad Resolving is incompatibel met de functie Instant on. Voor meer informatie over Onmiddellijk aan, zie Onmiddellijk.
>* Met Lazy Ad Resolving, terwijl het zoeken voorwaarts over een ad onderbreking, zullen de dichtste en onderbreking aan de vraagpositie tijdens het onderzoek worden opgelost.
>* Als er meerdere ad-hocafbrekingen tegelijk voorkomen (VMAP), worden deze tegelijkertijd opgelost.
>* Het wordt afgeraden de waarde *setDelayAdLoadingTolerance() *te verlagen tot onder de standaardwaarde (5 seconden). Hierdoor kan de speler onnodig &quot;bufferen&quot;.
>* Lazy ad Resolving heeft geen invloed op pre-roll advertenties.
>* Het luie Oplossen van Advertenties wordt momenteel gesteund met Auditude-Insteekmodule. Het wordt aanbevolen ** setDelayAdLoadingto niet in te stellen op true als u een aangepaste resolver gebruikt.

>


