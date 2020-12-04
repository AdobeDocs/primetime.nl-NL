---
description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
seo-description: De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.
seo-title: Toevoegen
title: Toevoegen
uuid: 75c1d77a-a7ff-4cb6-ad7f-7c83a950b7cb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Toevoegen {#ad-insertion}

De voorbeeldimplementatie illustreert hoe u de speler voor advertenties kunt instellen. Dit omvat het instellen van videometagegevens voor het invoegen en het omzetten van de pre-, mid- en postroladvertenties in VOD- of live/lineaire videostreams. Ook wordt getoond hoe klikbare advertenties kunnen worden afgehandeld.

Het instellen van een speler voor het invoegen van advertenties omvat:

* **Invoer:** invoerfeed vullen met metagegevens voor advertenties. Zie [Catalogusindeling](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Referentie-implementatiefeed-adapter:de invoerfeed** parseren om een advertentie-metagegevensobject te vullen.
* **AdsManager:AdsManager** gebruiken om de advertentiemetagegevens terug te winnen en overeenkomstige AdProvider tot stand te brengen.