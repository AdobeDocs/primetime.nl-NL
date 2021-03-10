---
description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
title: Toevoegen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Toevoegen {#ad-insertion}

De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.

Het instellen van een speler voor het invoegen van advertenties omvat:

* **Invoer:** invoerfeed vullen met metagegevens voor advertenties. Zie [Catalogusindeling](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Referentie-implementatiefeed-adapter:de invoerfeed** parseren om een advertentie-metagegevensobject te vullen.
* **AdsManager:AdsManager** gebruiken om de advertentiemetagegevens terug te winnen en overeenkomstige AdProvider tot stand te brengen.