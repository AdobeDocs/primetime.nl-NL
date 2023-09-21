---
title: Pakketmedia
description: Pakketmedia
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Pakketmedia {#package-media}

Gebruik het tabblad Media verpakken om inhoud te verpakken. In de sectie Eigenschappen van Packager worden de instellingen van Packager weergegeven die op het tabblad Voorkeuren zijn ingevoerd. Als u deze instellingen wilt wijzigen, gaat u naar het tabblad Voorkeuren, wijzigt u de instellingen en kiest u Opslaan.

Als u één FLV- of F4V-bestand in een pakket wilt plaatsen, kiest u de optie **[!UICONTROL Select Single File]** en voert u het volledige pad naar het bronbestand in en het volledige pad waar het gecodeerde bestand moet worden opgeslagen.

Als u alle bestanden in een map wilt verpakken, kiest u de optie **[!UICONTROL Select Single Folder]** -optie. Geef de map op die de bronbestanden bevat. Alleen bestanden in de invoermap die overeenkomen met de **[!UICONTROL Input Media File Selection]** criteria worden in een pakket opgenomen (bestanden in submappen worden niet in een pakket geplaatst). Kies of u wilt versleutelen [!DNL .flv] bestanden, [!DNL .f4v] of voer een aangepaste reguliere expressie in (bijvoorbeeld &quot;.&#42;&quot; worden alle bestanden in de map versleuteld). De gecodeerde bestanden worden opgeslagen in de opgegeven uitvoermap met dezelfde bestandsnaam als het oorspronkelijke bestand.

>[!NOTE]
>
>Bestandspaden moeten verwijzen naar bestanden die beschikbaar zijn op de pakketserver. Als u de Manager van de Flash Access op een verschillende machine dan de verpakkingsserver in werking stelt, moet u een weg specificeren die door de server (of op een netwerkaandrijving of op de server zelf wordt gevestigd) toegankelijk is.

In de volgende tabel worden de voorkeuren voor Media verpakken beschreven:

| Voorkeur | Beschrijving |
|---|---|
| Beleidsbestandsnaam/-namen | Selecteer een of meer beleidsregels in de vervolgkeuzelijst die u op de inhoud wilt toepassen. Als u meerdere beleidsregels wilt selecteren, houdt u de CTRL-toets ingedrukt terwijl u beleid selecteert. |
| Seconden niet gecodeerd | Geeft het aantal seconden aan dat de inhoud aan het begin van het bestand zonder codering moet worden weergegeven. Voer &quot;0&quot; in om te coderen vanaf het begin. |
| Video versleutelen | Schakel dit selectievakje in om videogegevens te versleutelen |
| Coderingsniveau | Selecteer het coderingsniveau voor videogegevens als videocodering is ingeschakeld. Met Hoog worden alle videogegevens gecodeerd. Delen van de video selectief coderen met Normaal en Laag. (Alleen voor F4V met H.264-video) |
| Audio versleutelen | Schakel dit selectievakje in om audiogegevens te versleutelen |
| Script versleutelen | Schakel dit selectievakje in om scriptgegevens te coderen (alleen FLV) |
| Aangepaste eigenschappen | Geef aangepaste eigenschappen op die u in de inhoud in het pakket wilt opnemen. Deze eigenschappen zijn beschikbaar voor de licentieserver bij het uitgeven van een licentie. (Optioneel) |

Klik op de knop **[!UICONTROL Package Media]** om de bestanden te verpakken.
