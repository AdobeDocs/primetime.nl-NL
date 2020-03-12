---
seo-title: Op tijd gebaseerde regels definiëren
title: Op tijd gebaseerde regels definiëren
uuid: 17c69869-ac81-4561-9fb6-b1c5c9c4006d
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Op tijd gebaseerde regels definiëren {#defining-time-based-rules}

Adobe Access maakt gebruik van &#39;zachte handhaving&#39; van op tijd gebaseerde licentiebeperkingen. Als een tijdrecht tijdens het afspelen van een video verloopt, wordt het afspelen standaard beperkt tot de volgende keer dat de videostream opnieuw wordt gemaakt (door het aanroepen `Netstream.stop()` en `Netstream.play()`).

Terwijl de zachte handhaving het standaardgedrag is, kunt u harde handhaving ook toelaten door één van de volgende taken uit te voeren:

* Zorg dat uw videospeler de licentie periodiek opvraagt om er zeker van te zijn dat geen van de tijdbeperkingen is verlopen. Dit kan worden verwezenlijkt door `DRMManager.loadVoucher(LOCAL_ONLY).`een foutencode te roepen wijst erop dat de lokaal-opgeslagen vergunning niet meer geldig is.
* Wanneer de gebruiker de knoop van de Pauze klikt, kunt u het huidige videotimestamp registreren en dan roepen `Netstream.stop().`wanneer de gebruiker de knoop van het Spel klikt, kunt u aan de geregistreerde plaats zoeken en dan roepen `Netstream.play()`.

## Begindatum {#start-date}

Hier geeft u de datum op waarna een licentie geldig is.

Voorbeeld van gebruik: Gebruik een absolute datum om inhoudsvergunningen vóór de beschikbaarheidsdatum van een activa uit te geven, of een &quot;embargo&quot;periode af te dwingen.

## Einddatum {#end-date}

Hiermee geeft u de datum op waarna een licentie vervalt.

Voorbeeld van gebruik: Gebruik een absolute vervaldatum om het einde van distributierechten te weerspiegelen.

## Relatieve einddatum {#relative-end-date}

Vermeld de vervaldatum van de vergunning, uitgedrukt in verhouding tot de verpakkingsdatum.

Voorbeeld van gebruik: In een geautomatiseerd verpakkingsproces gebruikt u één beleid met deze optie voor een reeks video&#39;s om de vervaldatum in te stellen op 30 dagen ten opzichte van de verpakkingsdatum.

## Duur van licentiecache {#license-caching-duration}

Geeft aan hoe lang een licentie op schijf in de lokale licentieserve van de client in cache kan worden geplaatst zonder dat de licentie opnieuw moet worden opgehaald van de licentieserver. U kunt ook een absolute datum/tijd opgeven waarna een licentie niet langer in de cache kan worden opgeslagen.

Nadat de vervaldatum van de cache is verstreken, is de licentie niet meer geldig en moet de client een nieuwe licentie aanvragen bij de licentieserver.

Voorbeeld van gebruik: Gebruik de duur van het in cache plaatsen van licenties om een vaste tijdsduur op te geven die geldig is voor een bepaalde licentie, zoals in een gebruiksgeval voor verhuur. Een verhuur van 30 dagen kan worden gespecificeerd (met vergunning caching) om de totale vergunningsduur te vermelden waarbinnen om de inhoud te verbruiken.

## Afspeelvenster {#playback-window}

Hiermee geeft u op hoe lang een licentie geldig is nadat deze voor het eerst wordt gebruikt om beveiligde inhoud af te spelen.

Voorbeeld van gebruik: Sommige bedrijfsmodellen staan een verhuurperiode van 30 dagen toe, maar wanneer het afspelen begint, moet het binnen 48 uur worden voltooid. Deze levensduur van 48 uur van de licentie wordt gedefinieerd als het afspeelvenster.

## Voorschriften voor synchronisatie {#requirements-for-synchronization}

Hiermee geeft u de frequentie op waarmee de client de status synchroniseert met de server. Als aan de client een out-of-band licentie is verleend (zonder dat er een licentieserver wordt gecontacteerd), kunnen gebruiksregels opgeven dat de client synchronisatieberichten naar de server moet verzenden om de veilige tijd van de client te synchroniseren en de status van de client aan de server te melden.

Het synchronisatiegedrag wordt bepaald gebruikend de volgende parameters:

* Start Interval — Geeft aan hoe lang er moet worden gewacht na de laatste succesvolle synchronisatie om een andere synchronisatieaanvraag te starten.
* Hard stopinterval — (optioneel). Afspelen niet toestaan als de synchronisatie niet binnen de opgegeven tijd is gelukt.
* Synchrone synchronisatiewaarschijnlijkheid forceren (optioneel). Mogelijkheid waarmee de client een synchronisatiebericht moet verzenden vóór het volgende begininterval.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Deze gebruiksregel wordt ondersteund door Adobe Access-clients versie 3.0 en hoger. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund. Zie [Minimale clientversie](../../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md).