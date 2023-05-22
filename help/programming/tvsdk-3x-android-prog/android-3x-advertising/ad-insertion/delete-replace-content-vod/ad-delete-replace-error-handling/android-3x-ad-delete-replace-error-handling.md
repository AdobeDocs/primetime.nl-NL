---
description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
title: Foutafhandeling voor verwijderen en vervangen van toevoegen
exl-id: 40d1cf67-df8c-4c5f-a1f2-defe3dd2b44a
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Foutafhandeling voor verwijderen en vervangen van toevoegen  {#ad-deletion-and-replacement-error-handling}

TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.

TVSDK wordt beheerd `timeRanges` fouten door standaardsamenvoegings- en herschikkingsprocessen. Eerst sorteert de speler door de klant gedefinieerde tijdbereiken op *begin* tijd. Op basis van deze sorteervolgorde voegt TVSDK aangrenzende bereiken samen en voegt deze bereiken samen als er subsets en snijpunten tussen de bereiken zijn.

TVSDK verwerkt tijdbereikfouten met de volgende opties:

* **Niet in orde** De tijdbereiken worden opnieuw gesorteerd door TVSDK.

* **Subset** TVSDK voegt de tijdbereiksubsets samen.

* **Doorsnede** TVSDK voegt de elkaar kruisende tijdbereiken samen.

* **Conflict bereik vervangen** TVSDK selecteert de vervangingsduur vanaf de oudste `timeRange` die in de conflicterende groep wordt weergegeven.

TVSDK handelt signalerende-wijze conflicten met advertentiemetagegevens op de volgende manieren af:

* Als de ad signalerende wijze met de tijd-waaier meta-gegevens in conflict brengt, heeft de tijd-waaier meta-gegevens altijd prioriteit.

   Als de ad-signaalmodus bijvoorbeeld is ingesteld als serverkaart of manifestaanwijzingen en er ook MARK-tijdbereiken zijn in de metagegevens van de advertentie, is het resulterende gedrag dat de bereiken zijn gemarkeerd en dat er geen advertenties zijn ingevoegd.
* Voor de waaiers van de VERVANGING, als de signalerende wijze als serverkaart of duidelijke aanwijzingen wordt geplaatst, worden de waaiers vervangen zoals gespecificeerd in de waaiers van de VERVANGING, en er is geen toevoeging door serverkaart of duidelijke aanwijzingen.

   Zie voor meer informatie de *Handeling signaalmodus/combinatie van metagegevens* tabel in [Effect op toevoeging en schrapping van advertentiemodus](../../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/delete-replace-content-vod/android-3x-signaling-mode-android.md).

Houd rekening met het volgende:

* Wanneer de server niet geldig is `AdBreaks`, genereert en verwerkt TVSDK een `NOPTimelineOperation` voor de lege AdBreak en er wordt geen advertentie afgespeeld.

* Hoewel C3 en delete/replacement alleen voor VOD moeten worden ondersteund, worden tijdbereiken ook verwerkt voor live streams als deze zijn opgegeven in de metagegevens voor advertenties.
