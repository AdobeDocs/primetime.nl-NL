---
description: De Primetime-naslaggids voor TVSDK is een Android-toepassing die is gebouwd rond de frameworks TVSDK en AVE.
title: De Primetime-referentieimplementatie maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# De Primetime-referentieimplementatie maken {#build-the-primetime-reference-implementation}

De Primetime-naslaggids voor TVSDK is een Android-toepassing die is gebouwd rond de frameworks TVSDK en AVE.

Het project Primetime Reference instellen en bouwen in Eclipse:

1. Download het ZIP-bestand van TVSDK Android en pak het uit in een map op een locatie die u zich herinnert.
1. Start Eclipse.
1. Selecteren **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. Selecteren **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. Klikken **[!UICONTROL Next]**.
1. Gebruik de **[!UICONTROL Browse]** om de **[!UICONTROL Root Directory]** veld met de map onder [!DNL samples/PrimetimeReference/src] waarnaar u het ZIP-bestand van TVSDK Android hebt uitgepakt.
1. Selecteer de volgende te importeren projecten: **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**.
1. Klikken **[!UICONTROL Finish]**.
1. Selecteren  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** om het project te bouwen.

   Deze stap is niet nodig als het project automatisch wordt opgezet om te bouwen.
1. Als u het testproject in de werkruimte zou willen omvatten, associeer het testproject met het project PrimetimeReference:
   1. Herhaal stap 3. tot en met 6.
   1. Selecteer het volgende project dat u wilt importeren: `PrimetimeReference\tests`.
   1. Klikken **[!UICONTROL Finish]**.

      Het testproject heeft een gebiedsdeel op het project CatalogActivity zodat moet u het testproject met het project associëren CatalogActivity.
   1. Klikken met rechtermuisknop **[!UICONTROL tests]** en kiest u **[!UICONTROL Properties]**.
   1. Selecteer de **[!UICONTROL Projects]** onder Java Build Path.
   1. Klikken **[!UICONTROL Add...]**
   1. Selecteer CatalogActivity.
   1. Klikken **[!UICONTROL OK]** om het project toe te voegen.
   1. Klikken **[!UICONTROL OK]** om de pagina Eigenschappen af te sluiten.
   1. Selecteren  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** om het project te bouwen.

      Deze stap is niet nodig als het project automatisch wordt opgezet om te bouwen.
