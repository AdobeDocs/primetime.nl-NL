---
description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
seo-description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
seo-title: Toevoegen
title: Toevoegen
uuid: 75c1d77a-a7ff-4cb6-ad7f-7c83a950b7cb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Toevoegen {#ad-insertion}

De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.

Het instellen van een speler voor het invoegen van advertenties omvat:

* **Invoer:** Een invoerfeed vullen met metagegevens voor advertenties. Zie [Catalogusindeling](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Referentie-implementatiefeed-adapter:** De invoerfeed parseren om een metagegevensobject voor een advertentie te vullen.
* **AdsManager:** Met AdsManager kunt u de metagegevens van de advertentie ophalen en de bijbehorende AdProvider maken.