---
description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-description: TVSDK verwerkt fouten in het tijdbereik op basis van het specifieke probleem door de onjuist gedefinieerde tijdbereiken samen te voegen of opnieuw te ordenen.
seo-title: Foutafhandeling voor verwijderen en vervangen van toevoegen
title: Foutafhandeling voor verwijderen en vervangen van toevoegen
uuid: 615f42b7-733a-49c4-bd7a-f14ad0d23fa0
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# Foutafhandeling voor verwijderen en vervangen van toevoegen {#ad-deletion-and-replacement-error-handling}

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

   Voor meer informatie, zie de *het Ondertekenen Wijze/de Lijst van het Gedrag* van de Combinatie van Meta-gegevens in [Effect op en toevoeging en schrapping van ad het signaleren wijze](../../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/delete-replace-content-vod/android-3x-signaling-mode-android.md).

Houd rekening met het volgende:

* Wanneer de server niet geldig terugkeert `AdBreaks`, produceert TVSDK en verwerkt een `NOPTimelineOperation` voor lege AdBreak, en geen voegt spelen.

* Hoewel C3 en delete/replacement alleen voor VOD moeten worden ondersteund, worden tijdbereiken ook verwerkt voor live streams als deze zijn opgegeven in de metagegevens voor advertenties.
