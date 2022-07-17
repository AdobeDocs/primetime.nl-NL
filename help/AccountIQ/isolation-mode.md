---
title: Rapporten weergeven in de isolatiemodus
description: 'Rapporten weergeven in de isolatiemodus voor Xfinity. '
source-git-commit: afa77dd0d7ffe38d353fed21dc9591b994b11193
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Rapporten delen weergeven in de isolatiemodus {#report-isolation-mode}

In de Wijze van de Isolatie, identificeren MVPDs (zoals, Xfinity) constant abonnees over apparaten, maar identificeren hun abonnees verschillend, gebaseerd op de programmeurs die zij met in wisselwerking staan. In de standaardmodus identificeren MVPD&#39;s voortdurend abonnees op verschillende apparaten, ongeacht de programmeurs.

Bijvoorbeeld, in het volgende beeld als abonnee B van een Wijze van de Isolatie MVPD (zoals, Xfinity) tot de inhoud toegang heeft die door twee verschillende programmeurs wordt aangeboden gebruikend het zelfde apparaat, dan zal MVPD verschillende herkenningstekens met de twee verschillende toegangspogingen associëren. Dus voor die programmeurs (L en M in het cijfer) en voor Account IQ, lijkt het dat er twee verschillende abonnees zijn die tot de inhoud toegang hebben. Nochtans, voor Standaard MVPD, als abonnee B tot inhoud toegang heeft die door twee verschillende programmeurs wordt aangeboden, dan zal MVPD één enkel toegangsidentificator voor beide toegangspogingen associëren. MVPDs (zoals, Xfinity) op de Wijze van de Isolatie identificeert niet constant een abonnee zelfs als de abonnee het zelfde apparaat over verschillende programmeurs gebruikt.

![](assets/isolation-diff-new.png)

*Afbeelding: De Wijze van de isolatie MVPD identificeert vier verschillende abonnees in plaats van twee*

Om de vervorming van gegevens te beheren (door de zelfde abonnee te identificeren die verschillend wordt gebaseerd op de toegang tot van verschillende programmeurs), beperkt de Wijze van de Isolatie de activiteit die over een programmeur aan de activiteit slechts op de toepassingen van die programmeur wordt gemeld. Voor de isolatiemodus in de bovenstaande afbeelding ziet Programmer L bijvoorbeeld alleen gegevens die zijn gebaseerd op de activiteit van Identities W en Y, waarbij de identiteiten X en Z worden genegeerd.

>[!IMPORTANT]
>
> Het nadeel is dat Programmer L wordt beroofd van het delen van informatie die over Abonnees A en B wordt verzameld wegens activiteit met om het even welke Programmer buiten L.

In de isolatiemodus worden alle berekeningen die zijn gemaakt voor het verkrijgen van de Sharing Scores en alle bijbehorende meetgegevens gemaakt met alleen de activiteit van de apparaten die worden gestreamd vanuit toepassingen die tot de geselecteerde programmeur en kanalen behoren.
De delende scores en waarschijnlijkheden worden berekend slechts gebruikend de stroom die van de momenteel geselecteerde kanalen begint.

Metrische gegevens weergeven in de isolatiemodus:

1. Selecteren **isolatiemodus** van de **MVPD&#39;s in segment** en selecteert u **Selectie toepassen**.

   ![](assets/xfinity-in-segment.gif)

   *Afbeelding: MVPD-selectie in isolatiemodus*

1. Selecteer de gewenste kanalen in het menu **Kanalen in segment** en selecteert u **Selectie toepassen**. Selecteer ook een [tijdkader](/help/AccountIQ/product-concepts.md#granularity-def).

   >[!IMPORTANT]
   >
   >Omdat het delen van accounts relevanter is bij het streamen in alle toepassingen van de programmeur, ziet u lagere scores voor delen en enige variatie in de meetwaarden in de isolatiemodus.

   ![](assets/aggregate-sharing-isolation.png)

   *Afbeelding: Het delen van waarschijnlijkheidsmeters in de wijze van de Isolatie*

   Uit bovenstaande cijfers blijkt dat slechts 6% van alle rekeningen wordt gedeeld; slechts 8 % van de inhoud wordt door deze 8 % geconsumeerd . De kanalen kunnen hun scores in de isolatiemodus vergelijken met die in de andere MVPD&#39;s. Daarom moet de informatie die door het gebruiken van de Wijze van de Isolatie wordt verkregen verschillend van de andere gegevens worden geïnterpreteerd.
