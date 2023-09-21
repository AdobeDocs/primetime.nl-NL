---
description: Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functies Lazy Ad Loading en Lazy Ad Resolving kunt u deze opstartvertraging verminderen.
keywords: Lazy;Adverteren;Toevoegen, laden
title: Lazy en oplossen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Overzicht {#lazy-ad-resolving}

Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functies Lazy Ad Loading en Lazy Ad Resolving kunt u deze opstartvertraging verminderen.

* Eenvoudig proces voor het oplossen en laden van bestanden:

   1. TVSDK downloadt manifest (playlist) en *oplossen* alle advertenties.
   1. TVSDK *laden* alle advertenties en plaatsen deze op de tijdlijn.
   1. TVSDK verplaatst de speler naar de status PREPARED en begint met afspelen van inhoud.

  De speler gebruikt de URL&#39;s in het manifest om de advertentie-inhoud (creatieven) te verkrijgen, zorgt ervoor dat de advertentie-inhoud een indeling heeft die TVSDK kan afspelen en dat TVSDK de advertenties op de tijdlijn plaatst. Dit basisproces voor het oplossen en laden van advertenties kan een onaanvaardbare lange wachttijd veroorzaken voor een gebruiker die wacht om zijn inhoud af te spelen, vooral als het manifest meerdere advertentie-URL&#39;s bevat.

* *Lazy advertentie laden*:

   1. TVSDK downloadt een afspeellijst en *oplossen* alle advertenties.
   1. TVSDK *laden* pre-rol advertenties, verplaatst de speler in de PREPARED status, en de inhoudsplayback begint.
   1. TVSDK *laden* de resterende advertenties en plaatst deze op de tijdlijn wanneer het afspelen plaatsvindt.

  Met deze functie wordt het basisproces verbeterd doordat de speler in de status PREPARED wordt geplaatst voordat alle advertenties worden geladen.

* *Lazy en oplossen*:

   1. TVSDK downloadt de afspeellijst.
   1. TVSDK verhelpt alle pre-roll-advertenties en laadt deze, verplaatst de speler naar de status PREPARED en begint de inhoud af te spelen.
   1. TVSDK lost de resterende advertenties op, laadt deze en plaatst ze op de tijdlijn terwijl het afspelen plaatsvindt.

  Lazy Ad Resolving bouwt voort op Lazy Ad Loading om voor nog snellere opstart toe te staan. Nadat TVSDK pre-roll-advertenties heeft geplaatst, wordt de speler naar de status PREPARED verplaatst en worden aanvullende advertenties opgelost en op de tijdlijn geplaatst.

>[!IMPORTANT]
>
>Factoren die in overweging moeten worden genomen met Lazy Ad die:
>
>* Lazy Ad Resolving is standaard ingeschakeld. Als u deze uitschakelt, worden alle advertenties opgelost voordat het afspelen wordt gestart.
>* Met Lazy Adv Resolving kunt u pas zoeken of tikken nadat alle advertenties zijn opgelost:
>
>    * De speler moet wachten op de `kEventAdResolutionComplete` -gebeurtenis voordat u zoekopdrachten of trucs toestaat.
>    * Als de gebruiker zoekbewerkingen of truc-afspeelbewerkingen probeert uit te voeren terwijl advertenties nog steeds worden opgelost, geeft TVSDK de opdracht `kECLazyAdResolutionInProgress` fout.
>    * Indien nodig moet de speler de scrubbalk bijwerken, *na* de `kEventAdResolutionComplete` gebeurtenis.
>
>* Lazy Ad Resolving is alleen voor VOD. Het werkt niet met LIVE-streams.
>* Lazy Adverteren is niet compatibel met de *Direct aan* gebruiken.
>
>  Zie instant-on voor meer informatie over Instant On.
>
>* Opgeloste advertentie zorgt ervoor dat het afspelen veel sneller begint, maar als er in de eerste 60 seconden van het afspelen een advertentie-einde optreedt, wordt deze mogelijk niet opgelost.
>* Lazy ad resolution does not have pre-roll ads.
