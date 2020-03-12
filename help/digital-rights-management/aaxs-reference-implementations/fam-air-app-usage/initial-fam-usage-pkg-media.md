---
seo-title: Pakketmedia
title: Pakketmedia
uuid: f6e877be-d916-4766-bc44-99891a3df3a8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Pakketmedia {#package-media}

Gebruik het tabblad Media verpakken om inhoud te verpakken. In de sectie Eigenschappen van Packager worden de instellingen van Packager weergegeven die op het tabblad Voorkeuren zijn ingevoerd. Als u deze instellingen wilt wijzigen, gaat u naar het tabblad Voorkeuren, wijzigt u de instellingen en kiest u Opslaan.

Als u één FLV- of F4V-bestand in een pakket wilt plaatsen, kiest u de **[!UICONTROL Select Single File]** optie en voert u het volledige pad in naar het bronbestand en het volledige pad waar het gecodeerde bestand moet worden opgeslagen.

Kies de **[!UICONTROL Select Single Folder]** optie als u alle bestanden in een map wilt verpakken. Geef de map op die de bronbestanden bevat. Alleen bestanden in de invoermap die aan de **[!UICONTROL Input Media File Selection]** criteria voldoen, worden in een pakket opgenomen (bestanden in submappen worden niet in een pakket geplaatst). Kies of u [!DNL .flv] bestanden of [!DNL .f4v] bestanden wilt versleutelen of voer een aangepaste reguliere expressie in (bijvoorbeeld &quot;.*&quot; codeert alle bestanden in de map). De gecodeerde bestanden worden opgeslagen in de opgegeven uitvoermap met dezelfde bestandsnaam als het oorspronkelijke bestand.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Bestandspaden moeten verwijzen naar bestanden die beschikbaar zijn op de pakketserver. Als u Flash Access Manager uitvoert op een andere computer dan de pakketserver, moet u een pad opgeven dat toegankelijk is voor de server (op een netwerkstation of op de server zelf).

In de volgende tabel worden de voorkeuren voor Media verpakken beschreven:

| Voorkeur | Beschrijving |
|---|---|
| Beleidsbestandsnaam/-namen | Selecteer een of meer beleidsregels in de vervolgkeuzelijst die u op de inhoud wilt toepassen. Als u meerdere beleidsregels wilt selecteren, houdt u de Ctrl-toets ingedrukt terwijl u beleid selecteert. |
| Seconden niet gecodeerd | Geeft het aantal seconden aan dat de inhoud aan het begin van het bestand zonder codering moet worden weergegeven. Voer &quot;0&quot; in om te coderen vanaf het begin. |
| Video versleutelen | Schakel dit selectievakje in om videogegevens te versleutelen |
| Coderingsniveau | Als videocodering is ingeschakeld, selecteert u het coderingsniveau voor videogegevens. Met Hoog worden alle videogegevens gecodeerd. Delen van de video selectief coderen met Normaal en Laag. (Alleen voor F4V met H.264-video) |
| Audio versleutelen | Schakel dit selectievakje in om audiogegevens te versleutelen |
| Script versleutelen | Schakel dit selectievakje in om scriptgegevens te coderen (alleen FLV) |
| Aangepaste eigenschappen | Geef aangepaste eigenschappen op die u in de inhoud van het pakket wilt opnemen. Deze eigenschappen zijn beschikbaar voor de licentieserver bij het uitgeven van een licentie. (Optioneel) |

Nadat de verpakkingsopties zijn geselecteerd, klikt u op de **[!UICONTROL Package Media]** knop om de bestanden te verpakken.
