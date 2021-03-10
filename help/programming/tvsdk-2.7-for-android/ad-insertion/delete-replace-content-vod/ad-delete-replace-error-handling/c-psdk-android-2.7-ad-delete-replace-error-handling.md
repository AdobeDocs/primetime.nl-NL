---
description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
title: Foutafhandeling voor verwijderen en vervangen van toevoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Overzicht {#ad-deletion-and-replacement-error-handling-overview}

TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.

TVSDK beheert `timeRanges` fouten door standaardsamenvoegings- en herschikkingsprocessen. Eerst sorteert de speler door de klant gedefinieerde tijdbereiken op basis van de *begin* tijd. Op basis van deze sorteervolgorde voegt TVSDK aangrenzende bereiken samen en voegt deze bereiken samen als er subsets en snijpunten tussen de bereiken zijn.

TVSDK verwerkt tijdbereikfouten met de volgende opties:

* **Buiten orderTVSDK** past de tijdwaaiers opnieuw aan.

* **Met** SubsetTVSDK worden de tijdbereiksubsets samengevoegd.

* **Met** IntersectTVSDK worden de elkaar kruisende tijdbereiken samengevoegd.

* **Vervang bereiken** conflictTVSDK selecteert de vervangingsduur van de oudste  `timeRange` die in de conflicterende groep verschijnt.

TVSDK handelt signalerende-wijze conflicten met advertentiemetagegevens op de volgende manieren af:

* Als de ad signalerende wijze met de tijd-waaier meta-gegevens in conflict brengt, heeft de tijd-waaier meta-gegevens altijd prioriteit.

   Als de ad-signaalmodus bijvoorbeeld is ingesteld als serverkaart of manifestaanwijzingen en er ook MARK-tijdbereiken zijn in de metagegevens van de advertentie, is het resulterende gedrag dat de bereiken zijn gemarkeerd en dat er geen advertenties zijn ingevoegd.
* Voor de waaiers van de VERVANGING, als de signalerende wijze als serverkaart of duidelijke aanwijzingen wordt geplaatst, worden de waaiers vervangen zoals gespecificeerd in de waaiers van de VERVANGING, en er is geen toevoeging door serverkaart of duidelijke aanwijzingen.

   Voor meer informatie, zie *De Wijze van het Ondertekenen / de Lijst van de Combinatie van Meta-gegevens* in [Effect op en toevoeging en schrapping van ad signalerende wijze..](../../../../tvsdk-2.7-for-android/ad-insertion/delete-replace-content-vod/c-psdk-android-2.7-signaling-mode-metadata-combos-android.md#c_psdk_signaling-mode-metadata-combos-android).

Houd rekening met het volgende:

* Als de server geen geldige `AdBreaks` retourneert, genereert en verwerkt TVSDK een `NOPTimelineOperation` voor de lege AdBreak en wordt geen advertentie afgespeeld.

* Hoewel C3 en delete/replacement alleen voor VOD moeten worden ondersteund, worden tijdbereiken ook verwerkt voor live streams als deze zijn opgegeven in de metagegevens voor advertenties.

