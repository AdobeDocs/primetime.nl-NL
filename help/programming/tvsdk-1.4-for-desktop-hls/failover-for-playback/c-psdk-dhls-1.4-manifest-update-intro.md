---
description: TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. TVSDK ondersteunt een dynamische set bitsnelheidprofielen die worden weergegeven of verdwijnen uit het hoofdmanifest, inclusief niet-overlappende bitsnelheden voor profielen tussen updates.
seo-description: TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. TVSDK ondersteunt een dynamische set bitsnelheidprofielen die worden weergegeven of verdwijnen uit het hoofdmanifest, inclusief niet-overlappende bitsnelheden voor profielen tussen updates.
seo-title: Live master-manifest bijwerken
title: Live master-manifest bijwerken
uuid: 44f8adc2-0538-4c5d-8e39-55f661d8540b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Live master-manifest bijwerken{#live-master-manifest-update}

TVSDK kan gewijzigde afspeelinformatie in master m3u8-manifests voor live streaming detecteren en de afspeelinformatie bijwerken terwijl de stream wordt afgespeeld. TVSDK ondersteunt een dynamische set bitsnelheidprofielen die worden weergegeven of verdwijnen uit het hoofdmanifest, inclusief niet-overlappende bitsnelheden voor profielen tussen updates.

De volgende functies worden ondersteund:

* Aantal profielen (verhogen of verlagen)
* Profielbitsnelheden (overlappend of niet-overlappend)
* Profielen met URL&#39;s op dezelfde (of andere) server
* Elke failoverstructuur

Aan alle volgende voorwaarden moet worden voldaan:

* Stream is live.
* Zowel de tijd als de tag veranderen.
* Alle vertoningsgegevens blijven hetzelfde (behalve dat URL&#39;s kunnen variëren).
* De DRM-toegangsgegevens blijven ongewijzigd.
* Segmenten worden verpakt rond dezelfde PTS- en framegrenzen in een klein foutbereik.

## Live master-manifest update-architectuur {#section_32254A0F684B4960ACC33BF6B1AEF6F1}

Hier volgt een aantal informatie en voorbeelden over hoe de TVSDK bijgewerkte hoofdmanifests aanpast.

Deze functie is standaard uitgeschakeld. Als de toepassing deze inschakelt door een updatefrequentie in minuten in te stellen, vinden de volgende stappen plaats na elk update-interval:

1. TVSDK controleert de laatste gewijzigde tijd en het etiket van het hoofdmanifest om te bepalen of het dossier is bijgewerkt.

   Als zowel de tijd als de tag zijn gewijzigd, wordt het bestand als gewijzigd beschouwd.
1. TVSDK parseert en analyseert het nieuwe manifest en neemt passende actie op basis van de aard van de update.
1. Als de huidige het spelen beetjetarief het beetjetarief van gewijzigd manifest aanpast, overschakelt TVSDK aan het nieuwe profiel.

   Het nieuwe profiel kan afkomstig zijn van een andere server of dezelfde server, met dezelfde bitsnelheid. In dit geval is de overgang vloeiend.
1. Als het huidige het spelen beetjetarief niet meer aanwezig in nieuw manifest is, probeert TVSDK om een beetjetarief in het huidige profiel te vinden dat ook in nieuw manifest bestaat.

   * Als een gelijke wordt gevonden, overschakelt de speler eerst aan het passende profiel van het beetjetarief in bestaand manifest en overschakelt aan het passende profiel van het beetjetarief in bijgewerkt manifest. Dit zorgt ervoor dat de overgang vloeiend verloopt.
   * Als er geen beetjetarief in gemeenschappelijk tussen vorig manifest en nieuw manifest is, of als TVSDK niet op het beetjetarief kan schakelen dat aanpast, de schakelaars TVSDK direct aan het laagste die tariefprofiel van nieuw manifest en gebruiksABR om aan om het even welk toelaatbare beetjetarief over te schakelen op bandbreedte wordt gebaseerd. Hierdoor kan het afspelen enigszins glitch zijn, maar dit heeft minimaal effect.

1. Als de update succesvol is, verzendt TVSDK een `MediaPlayerItemEvent.MASTER_UPDATED` gebeurtenis.
1. Als de update niet is gelukt, wordt het afspelen voortgezet met de installatie van vóór deze update.

### Voorbeeld 1 {#example_DB55F2B9D98741628C9B973E47A0B6A0}

De volgende bitsnelheden worden live uitgezonden:

* 500k
* 900k
* 2100k

De 2100k-stream heeft een aantal problemen en moet daarom opnieuw worden opgestart. Het hoofdmanifest wordt bijgewerkt en bevat slechts 500 kB en 900 kB. Kort daarna zullen de gebruikers die dit programma bij 2100 k bekijken een beetje tariefschakelaar aan 900 k krijgen. De gebruikers die op 900.000 uur kijken, blijven om 900.000 uur kijken. Later, hervat de stroom 2100k, en het wordt toegevoegd terug in hoofdmanifest. Enige tijd later, worden de gebruikers die bij 900k letten, en de bandbreedte hebben, overgeschakeld naar 2100k.

### Voorbeeld 2 {#example_485E9A9F373D454CADE5395DEC734E5D}

De volgende bitsnelheden worden live uitgezonden:

* 500k
* 900k
* 2100k

Al deze beetjetarieven moeten opnieuw worden begonnen. Hiervoor zijn twee tijdsstromen ingesteld, op 400 kbps en 1500 kbps. De gebruikers worden geschakeld aan 400k, die het laagste beetjetarief van de nieuwe configuratie is. Sommige gebruikers worden geschakeld naar 1500k wanneer hun bandbreedte voldoende is. Later, zijn de drie beetjetarieven file en hoofdmanifest wordt bijgewerkt. De gebruikers schakelen automatisch terug om bij 500k te letten, die de laagste bandbreedte in herzien (origineel) manifest is. Een tijdje later, worden de gebruikers geschakeld aan de hoogste bandbreedte (900k of 1200k) die hun netwerk toestaat.

## Live master-manifest bijwerken gebruiken {#section_34AC4A9751DB4B7C8561302C6A59A1C4}

U kunt deze functie inschakelen en controleren op verwante gebeurtenissen.

1. Als u live master-manifest-updates wilt inschakelen, stelt u de updatefrequentie (in minuten) in door de `NetworkConfiguration.masterUpdateInterval` eigenschap in te stellen.
1. U kunt succesvolle manifestupdates optioneel bijhouden door te luisteren naar de `MediaPlayerItemEvent.MASTER_UPDATED` gebeurtenis.

