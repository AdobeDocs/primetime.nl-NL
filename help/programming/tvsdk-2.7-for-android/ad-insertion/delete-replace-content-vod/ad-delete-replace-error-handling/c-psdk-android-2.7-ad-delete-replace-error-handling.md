---
description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
title: Foutafhandeling voor verwijderen en vervangen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Overzicht {#ad-deletion-and-replacement-error-handling-overview}

TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.

TVSDK wordt beheerd `timeRanges` fouten door standaardsamenvoegings- en herschikkingsprocessen. Eerst sorteert de speler door de klant gedefinieerde tijdbereiken op *begin* tijd. Op basis van deze sorteervolgorde voegt TVSDK aangrenzende bereiken samen en voegt deze bereiken samen als er subsets en snijpunten tussen de bereiken zijn.

TVSDK verwerkt tijdbereikfouten met de volgende opties:

* **Niet in orde** TVSDK rangschikt de tijdbereiken opnieuw.

* **Subset** TVSDK voegt de tijdbereiksubsets samen.

* **Doorsnede** TVSDK voegt de elkaar kruisende tijdbereiken samen.

* **Conflict bereik vervangen** TVSDK selecteert de vervangingsduur vanaf de oudste `timeRange` die in de conflicterende groep wordt weergegeven.

TVSDK handelt signalerende-wijze conflicten met advertentiemetagegevens op de volgende manieren af:

* Als de ad signalerende wijze met de tijd-waaier meta-gegevens in conflict brengt, heeft de tijd-waaier meta-gegevens altijd prioriteit.

  Als de ad-signaalmodus bijvoorbeeld is ingesteld als serverkaart of manifestaanwijzingen en er ook MARK-tijdbereiken zijn in de metagegevens van de advertentie, is het resulterende gedrag dat de bereiken zijn gemarkeerd en dat er geen advertenties zijn ingevoegd.
* Voor de waaiers van de VERVANGING, als de signalerende wijze als serverkaart of duidelijke aanwijzingen wordt geplaatst, worden de waaiers vervangen zoals gespecificeerd in de waaiers van de VERVANGING, en er is geen toevoeging door serverkaart of duidelijke aanwijzingen.

  Zie de klasse *Handeling signaalmodus/combinatie van metagegevens* tabel in [Effect op invoeging en verwijdering van advertentiemodus...](../../../../tvsdk-2.7-for-android/ad-insertion/delete-replace-content-vod/c-psdk-android-2.7-signaling-mode-metadata-combos-android.md#c_psdk_signaling-mode-metadata-combos-android).

Houd rekening met het volgende:

* Wanneer de server niet geldig retourneert `AdBreaks`, genereert en verwerkt TVSDK een `NOPTimelineOperation` voor de lege AdBreak, en geen advertentie speelt.

* Hoewel C3 en delete/replacement alleen voor VOD moeten worden ondersteund, worden tijdbereiken ook verwerkt voor live streams als deze zijn opgegeven in de metagegevens voor advertenties.
