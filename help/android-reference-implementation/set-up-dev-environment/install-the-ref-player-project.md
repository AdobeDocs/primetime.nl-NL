---
description: De Primetime-naslaggids voor TVSDK is een Android-toepassing die is gebouwd rond de frameworks TVSDK en AVE.
title: De implementatie van de Primetime-referentie samenstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 1%

---


# De Primetime-referentie-implementatie {#build-the-primetime-reference-implementation} samenstellen

De Primetime-naslaggids voor TVSDK is een Android-toepassing die is gebouwd rond de frameworks TVSDK en AVE.

Het project Primetime Reference instellen en bouwen in Eclipse:

1. Download het ZIP-bestand van TVSDK Android en pak het uit in een map op een locatie die u zich herinnert.
1. Start Eclipse.
1. Selecteer **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. Selecteer **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. Klik op **[!UICONTROL Next]**.
1. Gebruik de knop **[!UICONTROL Browse]** om het veld **[!UICONTROL Root Directory]** te vullen met de map onder [!DNL samples/PrimetimeReference/src] waarnaar u het ZIP-bestand van TVSDK Android hebt uitgepakt.
1. Selecteer de volgende te importeren projecten: **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**.
1. Klik op **[!UICONTROL Finish]**.
1. Selecteer **[!UICONTROL Project]** > **[!UICONTROL Build Project]** om het project te bouwen.

   Deze stap is niet nodig als het project automatisch wordt opgezet om te bouwen.
1. Als u het testproject in de werkruimte zou willen omvatten, associeer het testproject met het project PrimetimeReference:
   1. Herhaal stap 3. tot en met 6.
   1. Selecteer het volgende project dat u wilt importeren: `PrimetimeReference\tests`.
   1. Klik op **[!UICONTROL Finish]**.

      Het testproject heeft een gebiedsdeel op het project CatalogActivity zodat moet u het testproject met het project associëren CatalogActivity.
   1. Klik met de rechtermuisknop **[!UICONTROL tests]** en kies **[!UICONTROL Properties]**.
   1. Selecteer het tabblad **[!UICONTROL Projects]** onder Java Build Path.
   1. Klik op **[!UICONTROL Add...]**
   1. Selecteer CatalogActivity.
   1. Klik **[!UICONTROL OK]** om het project toe te voegen.
   1. Klik **[!UICONTROL OK]** om de pagina van Eigenschappen weg te gaan.
   1. Selecteer **[!UICONTROL Project]** > **[!UICONTROL Build Project]** om het project te bouwen.

      Deze stap is niet nodig als het project automatisch wordt opgezet om te bouwen.
