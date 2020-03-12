---
description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-title: Foutafhandeling voor verwijderen en vervangen van toevoegen
title: Foutafhandeling voor verwijderen en vervangen van toevoegen
uuid: 9a951bc4-b372-4655-8510-3f474171415d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# Overzicht {#ad-deletion-and-replacement-error-handling-overview}

TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.

TVSDK beheert `timeRanges` fouten door standaardsamenvoegings- en herschikkingsprocessen. Eerst sorteert de speler door de klant gedefinieerde tijdbereiken op de *begintijd* . Op basis van deze sorteervolgorde voegt TVSDK aangrenzende bereiken samen en voegt deze bereiken samen als er subsets en snijpunten tussen de bereiken zijn.

TVSDK verwerkt tijdbereikfouten met de volgende opties:

* **De tijdbereiken worden opnieuw gesorteerd in de volgorde** van TVSDK.

* **Met de subset** TVSDK worden de subsets van het tijdbereik samengevoegd.

* **Met Doorsnede** van TVSDK worden de elkaar kruisende tijdbereiken samengevoegd.

* **Bij Vervangen worden bereiken conflicteert** TVSDK de vervangduur vanaf de vroegste `timeRange` die in de conflicterende groep wordt weergegeven.

TVSDK handelt signalerende-wijze conflicten met advertentiemetagegevens op de volgende manieren af:

* Als de ad signalerende wijze met de tijd-waaier meta-gegevens in conflict brengt, heeft de tijd-waaier meta-gegevens altijd prioriteit.

   Als de ad-signaalmodus bijvoorbeeld is ingesteld als serverkaart of manifestaanwijzingen en er ook MARK-tijdbereiken zijn in de metagegevens van de advertentie, is het resulterende gedrag dat de bereiken zijn gemarkeerd en dat er geen advertenties zijn ingevoegd.
* Voor de waaiers van de VERVANGING, als de signalerende wijze als serverkaart of duidelijke aanwijzingen wordt geplaatst, worden de waaiers vervangen zoals gespecificeerd in de waaiers van de VERVANGING, en er is geen toevoeging door serverkaart of duidelijke aanwijzingen.

   Zie de tabel Gedragingen *voor* signaalmodus/metagegevenscombinatie in [Effect op invoeging en verwijdering van de advertentiemodus voor meer informatie...](../../../../tvsdk-2.7-for-android/ad-insertion/delete-replace-content-vod/c-psdk-android-2.7-signaling-mode-metadata-combos-android.md#c_psdk_signaling-mode-metadata-combos-android).

Houd rekening met het volgende:

* Wanneer de server niet geldig terugkeert `AdBreaks`, produceert TVSDK en verwerkt een `NOPTimelineOperation` voor lege AdBreak, en geen voegt spelen.

* Hoewel C3 en delete/replacement alleen voor VOD moeten worden ondersteund, worden tijdbereiken ook verwerkt voor live streams als deze zijn opgegeven in de metagegevens voor advertenties.

