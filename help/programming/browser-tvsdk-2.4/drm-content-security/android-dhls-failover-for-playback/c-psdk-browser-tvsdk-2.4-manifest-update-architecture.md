---
description: Hier volgt een aantal informatie en voorbeelden over hoe Browser TVSDK bijgewerkte master manifesten aanpast.
seo-description: Hier volgt een aantal informatie en voorbeelden over hoe Browser TVSDK bijgewerkte master manifesten aanpast.
seo-title: Live master-manifest updatearchitectuur
title: Live master-manifest updatearchitectuur
uuid: 6f253502-8dec-4b42-9ee1-99ad9bfd6080
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 1%

---


# Live master-manifest updatearchitectuur{#live-master-manifest-update-architecture}

Hier volgt een aantal informatie en voorbeelden over hoe Browser TVSDK bijgewerkte master manifesten aanpast.

Deze functie is standaard uitgeschakeld. Als de toepassing deze inschakelt door een updatefrequentie in minuten in te stellen, vinden de volgende stappen plaats na elk update-interval:

1. De Browser TVSDK controleert de laatste gewijzigde tijd en de tag van het master manifest om te bepalen of het bestand is bijgewerkt.

   Als zowel de tijd als de tag zijn gewijzigd, wordt het bestand als gewijzigd beschouwd.
1. Browser TVSDK ontleedt en analyseert nieuw manifest en neemt aangewezen actie die op de aard van de update wordt gebaseerd.
1. Als de huidige afspeelbitsnelheid overeenkomt met de bitsnelheid van het gewijzigde manifest, schakelt de TVSDK-browser over naar het nieuwe profiel.

   Het nieuwe profiel kan afkomstig zijn van een andere server of dezelfde server, met dezelfde bitsnelheid. In dit geval is de overgang vloeiend.
1. Als de huidige het spelen beetjetarief niet meer in nieuw manifest aanwezig is, probeert Browser TVSDK om een beetjetarief in het huidige profiel te vinden dat ook in nieuw manifest bestaat.

   * Als een gelijke wordt gevonden, schakelt de speler eerst naar het passende profiel van het beetjetarief in bestaand manifest en overschakelt naar het passende profiel van het beetjetarief in bijgewerkt manifest. Dit zorgt ervoor dat de overgang vloeiend verloopt.
   * Als er geen beetjetarief in gemeenschappelijk tussen vorig manifest en nieuw manifest is, of als Browser TVSDK niet op het beetjetarief kan schakelen dat aanpast, de Browser TVSDK schakelaars direct aan het laagste de tariefprofiel van nieuw manifest en gebruikt ABR om aan om het even welk toelaatbare beetjetarief over te schakelen dat op bandbreedte wordt gebaseerd. Hierdoor kan het afspelen enigszins glitch zijn, maar dit heeft minimaal effect.

1. Als de update succesvol is, verzendt Browser TVSDK een `MediaPlayerItemEvent.MASTER_UPDATED` gebeurtenis.
1. Als de update niet is gelukt, wordt het afspelen voortgezet met de installatie van vóór deze update.

## Voorbeeld 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

De volgende bitsnelheden worden live uitgezonden:

* 500 kB
* 900 kB
* 2100 kB

De 2100k-stream heeft een aantal problemen en moet daarom opnieuw worden opgestart. Het master manifest wordt bijgewerkt en bevat slechts 500 kB en 900 kB. Kort daarna zullen de gebruikers die dit programma bij 2100 k bekijken een beetje tariefschakelaar aan 900 k krijgen. De gebruikers die op 900.000 uur kijken, blijven om 900.000 uur kijken. Later, hervat de stroom 2100k, en het wordt toegevoegd terug in master manifest. Enige tijd later, worden de gebruikers die bij 900k letten, en de bandbreedte hebben, overgeschakeld naar 2100k.

### Voorbeeld 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

De volgende bitsnelheden worden live uitgezonden:

* 500 kB
* 900 kB
* 2100 kB

Al deze beetjetarieven moeten opnieuw worden begonnen. Hiervoor zijn twee tijdsstromen ingesteld, op 400 kbps en 1500 kbps. De gebruikers worden geschakeld aan 400k, die het laagste beetjetarief van de nieuwe configuratie is. Sommige gebruikers worden geschakeld naar 1500k wanneer hun bandbreedte voldoende is. Later, zijn de drie beetjetarieven file en master manifest wordt bijgewerkt. De gebruikers schakelen automatisch terug om bij 500k te letten, die de laagste bandbreedte in herzien (origineel) manifest is. Een tijdje later, worden de gebruikers geschakeld aan de hoogste bandbreedte (900k of 1200k) die hun netwerk toestaat.

<!-- 

WRITER: Add relref to api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#MASTER_UPDATED

 -->

