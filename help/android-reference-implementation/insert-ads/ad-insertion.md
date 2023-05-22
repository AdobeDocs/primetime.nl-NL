---
description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
title: Toevoegen
exl-id: 3c2d8fca-2a0e-4577-81f3-7b390f6396e1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Toevoegen {#ad-insertion}

De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.

Het instellen van een speler voor het invoegen van advertenties omvat:

* **Invoer:** Een invoerfeed vullen met metagegevens voor advertenties. Zie [Catalogusindeling](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Referentie-implementatiefeed-adapter:** De invoerfeed parseren om een metagegevensobject voor een advertentie te vullen.
* **AdsManager:** Met AdsManager kunt u de metagegevens van de advertentie ophalen en de bijbehorende AdProvider maken.
