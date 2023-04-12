---
title: Informatie exporteren voor accounts met hoge score voor delen
description: Exporteer gegevens voor accounts met een hoge score voor delen.
exl-id: df41ddd2-fde3-4861-abd4-6e32f0be9ea5
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 1%

---

# Informatie exporteren voor accounts met hoge score voor delen {#export-account-info-high-score}

De IQ van de rekening geeft u de optie om rekening het delen details voor hoogste 1000 abonneerekeningen uit te voeren die op hun worden gebaseerd [waarschijnlijkheid delen](/help/AccountIQ/product-concepts.md#account-sharing-probability-def). De gegevens in het geëxporteerde CSV-bestand worden gesorteerd in afnemende volgorde van de waarschijnlijkheid dat gebruikers hun abonnement gebruiken, van de geselecteerde MVPD&#39;s in de [segment](/help/AccountIQ/product-concepts.md#segment-def)voor een [opgegeven tijdsduur](/help/AccountIQ/product-concepts.md#time-frame-def).

De optie voor het exporteren van de gegevens voor het delen van accounts is beschikbaar op [Algemene verbruiksrapporten](/help/AccountIQ/general-usage-reports.md) en [Rapporten over gedeelde accounts](/help/AccountIQ/shared-acc-reports.md) pagina&#39;s.

>[!NOTE]
>
>De nummers in het gedownloade CSV-bestand verschillen van die in de rapporten Algemeen gebruik en Gedeelde accounts. De reden hiervoor is dat de pagina Algemene verbruiksrapporten aanvullende filters bevat waarmee de programmeurs Drempel kunnen selecteren voor het aantal apparaten, IP&#39;s en Zip-codes. De gegevens die worden geëxporteerd uit de rapporten Algemeen verbruik, zijn dus gebaseerd op het extra toegepaste drempelfilter.

![Exportoptie bij algemeen gebruik](assets/export.png)

De gegevens over het delen van accounts van abonnees exporteren:

1. Een gewenst segment definiëren na de stappen in [Segment definiëren en tijdframe selecteren](/help/AccountIQ/howto-select-segment-timeframe.md) ter evaluatie van [segment en tijdframe](/help/AccountIQ/segments-timeframe.md) deelvenster.

1. Selecteer **Bovenste 1000-accounts exporteren** optie om de rekeninginformatie voor 1000 abonnees met de hoogste waarschijnlijkheid van het delen uit te voeren.

Wanneer u de exportoptie gebruikt, worden de statistieken voor 1000 accounts met de hoogste waarschijnlijkheid dat ze met anderen delen (voor een bepaald tijdkader) gedownload naar de map Downloads op uw lokale computer.

>[!NOTE]
>
>Het gedownloade CSV-bestand kan worden geopend met elke toepassing die het CSV-bestand leest, bijvoorbeeld Microsoft Excel.

![geëxporteerde gegevens in CSV-indeling](assets/exported-csv.png)

*Afbeelding: Geëxporteerde gegevens van gedeelde accounts in CSV-indeling*

## Kolommen in het geëxporteerde rapport {#columns-in-export}

**Week/Maand**

De week of maand die u hebt geselecteerd in het dialoogvenster **Korreligheid en tijdkader** optie in de segmentselecteur, waarvoor de het delen statistieken worden gezocht.

**MVPD**

Als u een programmeergebruiker bent, toont de kolom aan welk MVPD de abonneerekening tot behoort.

**Abonnee-id**

Het gaat hier om een specifieke rekening.

**Minimum aantal apparaten**

Het daadwerkelijke aantal apparaten (die stroominhoud) is bijna zeker groter dan het minimumaantal apparaten, gespecificeerd voor een bepaalde rekening.

>[!NOTE]
>
>Het werkelijke aantal apparaten (dat streaminhoud) is zeker groter dan het minimale aantal apparaten dat voor een bepaalde account is opgegeven.

**Minimum aantal personen**

Het absolute minimum aantal mensen dat actieve het stromen inhoud gebruikend die apparaten was.

>[!NOTE]
>
>Het feitelijke aantal personen (dat stroominhoud) is vrijwel zeker veel groter dan het minimum aantal personen dat voor een bepaalde account is opgegeven.

**Aantal IP&#39;s**

Aantal IP adressen waarvan de inhoud wordt gestroomd.

**# Locaties**

Aantal locaties (op basis van postcode) vanwaar inhoud wordt gestreamd.

**Aantal plaatsen**

Aantal steden waar de streaming heeft plaatsgevonden.

**Aantal statussen**

Aantal staten waar het stromen heeft plaatsgevonden.

**Aantal clusters**

Het aantal afzonderlijke [clusters](/help/AccountIQ/product-concepts.md#cluster-def) waar streaming heeft plaatsgevonden.

**Geografisch bereik (mijl)**

De maximale afstand tussen de streaminglocaties die aan de account zijn gekoppeld.

**# AuthN OK**

Het aantal keren dat de gebruikers zich tijdens de periode hebben aangemeld, gebruikend die rekening.

**# AuthZ OK**

Aantal keren dat een MVPD een stroom, of toegang (tot inhoud), aan die rekening heeft verleend.

>[!NOTE]
>
>De **# AuthZ OK** is gerelateerd aan de **# Aanvragen afspelen**; het is kleiner dan de **# Aanvragen afspelen** omdat Adobe de vergunningen die voor MVPDs typisch voor 24 uren in het voorgeheugen onderbrengt.

**# Aanvragen afspelen**

Het werkelijke aantal streams tijdens de tijdsperiode.

**Aantal kanalen**

Het totale aantal verschillende kanalen dat de account gedurende de periode heeft gecontroleerd.

>[!NOTE]
>
>**Aantal kanalen** omvat de kanalen die niet noodzakelijk tot het programma geopende programmeur behoorden.
>
>Dit nummer voor de account is weergegeven omdat de account uw kanaal heeft gecontroleerd, maar tijdens die periode ook andere kanalen heeft geopend.

**Gebruikspatroon**

De aantallen in deze kolom zijn herkenningstekens die aan één van de 14 patronen in kaart brengen die wij alle gebruikersrekeningen als identificeren.

*Tabel: Gebruikspatroon-id&#39;s in geëxporteerde CSV-toewijzing met gebruikspatronen*

| ID | 1 | 2 | 3 | 4 | 5 en 8 | 6 | 7 | 9 | 10 en 11 | 12 | 13 | 14 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Gebruikspatronen | Gewone gebruiker | Reiziger of pendelaar | Grote familie | Familie en vrienden sluiten | Delen van sociale groepen | Grote groep vrienden | Gelijktijdige streaming | Delen door Gemeenschap | Onduidelijk gedrag | Kleine familie | Tweede thuis | Abnormaal gebruik |

{style="table-layout:auto"}

**Deelbaarheid**

Het delen van waarschijnlijkheid is de waarschijnlijkheid dat de specifieke rekening zijn geloofsbrieven deelt.

>[!NOTE]
>
> Het gemiddelde van de waarschijnlijkheid van delen van alle rekeningen (in het geselecteerde segment) wordt gebruikt om het [deelniveau](/help/AccountIQ/dashboard.md#sharing-level) van de [Geaggregeerde score voor delen](/help/AccountIQ/dashboard.md#aggregated-sharing).
