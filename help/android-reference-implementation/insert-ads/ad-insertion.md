---
description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
title: Toevoegen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
