---
seo-title: Op tijd gebaseerde regels
title: Op tijd gebaseerde regels
uuid: 19a6ee7e-9580-48bb-a3a6-ff2cedcc796a
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Op tijd gebaseerde regels {#time-based-rules}

Primetime DRM gebruikt &#39;zachte handhaving&#39; van op tijd gebaseerde licentiebeperkingen. Als een tijdrecht tijdens het afspelen van een video verloopt, is het standaardgedrag van Primetime DRM om het afspelen niet te beperken tot de volgende keer dat de videostream opnieuw wordt gemaakt (door `Netstream.stop()` en `Netstream.play()` aan te roepen).

Terwijl de zachte handhaving het standaardgedrag is, kunt u harde handhaving ook toelaten door één van de volgende taken uit te voeren:

* Zorg dat uw videospeler de licentie periodiek opvraagt om er zeker van te zijn dat geen van de tijdbeperkingen is verlopen. Dit kan worden verwezenlijkt door `DRMManager.loadVoucher(LOCAL_ONLY).` te roepen een foutencode wijst erop dat de lokaal-opgeslagen vergunning niet meer geldig is.
* Wanneer de gebruiker **[!UICONTROL Pause]** klikt, kunt u de huidige videotijdstempel opnemen en dan `Netstream.stop()` roepen. Wanneer de gebruiker de knoop van het Spel klikt, kunt u aan de geregistreerde plaats zoeken en dan `Netstream.play()` roepen.

## Begindatum {#start-date}

De begindatum geeft de datum aan waarna een licentie geldig is.

Voorbeeld van gebruik: Gebruik een absolute datum om inhoudsvergunningen vóór de beschikbaarheidsdatum van een activa uit te geven, of een &quot;embargo&quot;periode af te dwingen.

## Einddatum {#end-date}

De einddatum geeft de datum aan waarna een licentie vervalt.

Voorbeeld van gebruik: Gebruik een absolute vervaldatum om het einde van distributierechten te weerspiegelen.

## Relatieve einddatum {#relative-end-date}

De relatieve einddatum geeft de vervaldatum van de vergunning aan, die wordt uitgedrukt in verhouding tot de verpakkingsdatum en niet in verhouding tot de datum waarop de vergunning is afgegeven.

Voorbeeld van gebruik: Gebruik in een geautomatiseerd verpakkingsproces één Primetime DRM-beleid met deze optie voor een reeks video&#39;s om de vervaldatum in te stellen op 30 dagen ten opzichte van de verpakkingsdatum.

## Duur van licentiecache{#license-caching-duration}

De duur van het in cache plaatsen van licenties bepaalt hoe lang een licentie op schijf in de lokale licentieserve van de client in cache kan worden geplaatst zonder dat de licentie opnieuw moet worden opgehaald van de licentieserver. U kunt ook een absolute datum en tijd opgeven waarna een licentie niet langer in de cache kan worden opgeslagen.

Nadat de vervaldatum van de cache is verstreken, is de licentie niet meer geldig en moet de client een nieuwe licentie aanvragen bij de licentieserver.

Voorbeeld van gebruik: Gebruik de duur van het in cache plaatsen van licenties om een vaste tijdsduur op te geven die geldig is voor een bepaalde licentie, zoals in een gebruiksgeval voor verhuur. U kunt een verhuur van 30 dagen opgeven (met licentiecache) om de totale licentieduur aan te geven waarbinnen de inhoud moet worden geconsumeerd.

## Afspeelvenster {#playback-window}

In het afspeelvenster wordt aangegeven hoe lang een licentie geldig is nadat deze voor het eerst wordt gebruikt om beveiligde inhoud af te spelen.

Voorbeeld van gebruik: Sommige bedrijfsmodellen staan een verhuurperiode van 30 dagen toe, maar wanneer het afspelen begint, moet het afspelen binnen 48 uur worden voltooid. In dit geval is de duur van 48 uur van de licentie het afspeelvenster.

**Vanaf versie 5.3 voorwaarts**  - Het playbackvenster steunt ook de optie om Harde Stop toe te laten of onbruikbaar te maken, die erop wijst of de decryptiefcontext voor playback bij de afloop van het (toegelaten) playbackvenster zou moeten stoppen of ondanks afloop (gehandicapt) zou moeten voortzetten.

>[!NOTE]
>
>De optie voor vastzetten werkt niet correct met het afspeelvenster als dit wordt gebruikt in combinatie met dit venster (het afspeelvenster wordt niet ondersteund). Als u inhoud afspeelt in het afspeelvenster zonder beveiligde stop, wordt de beperking voor het afspeelvenster gerespecteerd.