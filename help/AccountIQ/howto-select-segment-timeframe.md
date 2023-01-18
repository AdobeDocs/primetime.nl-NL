---
title: Een segment en tijdframe definiëren
description: Een segment en tijdframe definiëren
exl-id: 86fe010d-3202-4ce2-b803-ff44f5538d7e
source-git-commit: c17fb003d8c8103aac36696f696c9e3c7bb83c4f
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Een segment en tijdframe definiëren {#define-segment}

Alle analyse of het bekijken rapporten in IQ van de Rekening beginnen met het bepalen van segment en het selecteren van tijdkader voor evaluatie. [Segment](/help/AccountIQ/product-concepts.md#segmet-def) verwijst naar alle abonnees of kijkers die aan uw criteria (het intekenen aan MVPD en het bekijken van specifieke kanalen) van evaluatie voldoen.

![](assets/segment-panel.png)

*Afbeelding: Selectie van segment en tijdkader*

Bij de bovenkant van alle rapportpagina&#39;s in Rekening IQ, is er een paneel om segment te bepalen door MVPDs, kanaalprogrammeurs, en granulariteit en tijdkader te selecteren.

## Segmentselectie {#select-segment}

### MVPD&#39;s selecteren in segment {#select-segment-mvpds}

MVPD&#39;s selecteren vanuit **MVPD&#39;s in segment** optie:

1. Klik of tik op **MVPD&#39;s in segment** vervolgkeuzelijst.

   >[!NOTE]
   >
   >**Alles** industrie MVPDs wordt geselecteerd door gebrek. Van hier kunt u een van de **De hoogste 10 MVPDs door score te delen**, **De hoogste 10 MVPDs door gebruik**, **Top 10 MVPD&#39;s per account**, of individuele MVPD&#39;s. Als u echter afzonderlijke MVPD&#39;s wilt selecteren, moet u de selectie opheffen **Alles**.

1. Klik of tik gewenste MVPDs.

   U kunt een MVPD uit de selectie verwijderen door het uit te schakelen.

1. Klikken of tikken **Selectie toepassen** zodat uw selectie van kracht wordt. Anders verliest u de gemaakte selectie.

   >[!NOTE]
   >
   >Als u de modus Isolatie selecteert, kan geen van de andere MVPD&#39;s worden geselecteerd.

### Kanalen in segment selecteren {#select-segment-channels}

Om de gewenste programmeerkanalen van te selecteren **Kanalen in segment** optie:

1. Klik of tik op **Kanalen in segment** vervolgkeuzelijst.

   >[!NOTE]
   >
   >**Alles** programmeerkanalen voor uw bedrijf worden geselecteerd door gebrek. Als u afzonderlijke kanalen of programmeurs wilt selecteren, moet u eerst de selectie opheffen **Alles**.

1. Klik of tik op de gewenste kanalen of programmeurs.

   De lijstitems op het hoogste niveau in het dialoogvenster **Kanalen in segment** zijn [programmeur](/help/AccountIQ/product-concepts.md#programmer-def) bedrijven en de lijstonderdelen onder programmeernamen zijn hun [kanalen](/help/AccountIQ/product-concepts.md#channel-def). U kunt of individuele kanalen selecteren onder programmeurs, of programmeurs selecteren en alle activiteiten van de kanalen onder die programmeur zijn inbegrepen in rapport en grafiekresultaten.

   ![](assets/programmer-channels.png)


   *Afbeelding: Programmeurs en kanalen die in kanaalselecteur worden vermeld*

   >[!IMPORTANT]
   >
   >De resultaten van het selecteren van afzonderlijke kanalen onder een programmeur zijn niet hetzelfde als die van het selecteren van de programmeur.
   >
   >
   >Wanneer u afzonderlijke kanalen selecteert, worden de activiteiten van die kanalen in bepaalde rapporten afzonderlijk uitgesplitst. Wanneer u echter de bovenliggende programmeur van al die kanalen selecteert, wordt alle activiteit van die kanalen opgenomen, maar niet afzonderlijk in rapporten onderverdeeld.

1. Klikken of tikken **Selectie toepassen** zodat uw selectie van kracht wordt.

>[!NOTE]
>
>U kunt niet meer dan 10 punten in de MVPD of programmeur pulldown menu&#39;s selecteren.

### Schakel MVPD&#39;s en kanalen uit {#deselect-segment-mvpds-channels}

Naast het wijzigen van de selectie in het dialoogvenster **MVPD&#39;s in segment** en **Kanalen in segment** segmentkiezers kunt u de eerder geselecteerde MVPD&#39;s en kanalen deselecteren door:

* Het selecteren van **Verwijderen** icon (![pictogram verwijderen](assets/remove-icon.png)) op de namen van deze geselecteerde MVPD&#39;s en kanalen die onder segmentkiezer worden weergegeven.

* U kunt ook **Selectie wissen** om alle eerder geselecteerde MVPD&#39;s of kanalen te verwijderen.

![](assets/segment-panel-selection.png)

*Afbeelding: Geselecteerde MVPD&#39;s en kanalen in segment- en tijdlijnpaneel*

## Korreligheid en selectie van tijdframes {#granularity-timeframe}

Een evaluatieperiode selecteren:

1. Selecteer **Korreligheid en tijdkader** datumkiezer.

1. Selecteer **Week** of **Maand** van **Samenvoegen met** om granulariteit voor uw evaluatie in te stellen.

   ![](assets/granularity-timeframe-weekwise.png)


   *Afbeelding: De kiezer van de datum om Korreligheid en tijdkader te selecteren*

1. Als u de granulariteit hebt geselecteerd, kunt u met de pijlen naar voren of naar achteren in de tijd gaan.

1. Geef een tijdsperiode op in het verleden (in maand of week op basis van geselecteerde granulariteit) voor evaluatie.

1. Selecteren **Selectie toepassen** om ervoor te zorgen dat de selectie van kracht wordt.
