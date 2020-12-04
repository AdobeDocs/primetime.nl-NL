---
description: U kunt eenvoudig een aangepaste gebruikersinterface maken op basis van het referentie-implementatieframework.
seo-description: U kunt eenvoudig een aangepaste gebruikersinterface maken op basis van het referentie-implementatieframework.
seo-title: Een aangepaste gebruikersinterface maken
title: Een aangepaste gebruikersinterface maken
uuid: b785f6a4-3ef8-4f7a-a087-0d6551da9750
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# Een aangepaste gebruikersinterface maken {#build-a-custom-user-interface}

U kunt een aangepaste gebruikersinterface maken op basis van het framework voor referentie-implementatie.

De UI-componenten van de volgende functies zijn al geïntegreerd:

* Klikbare advertenties
* Advertentie-overlays
* Geluid met late binding
* Ondertiteling
* Listeners voor alle bovenstaande componenten

1. Bewerk het bestand [!DNL PlayerFragment.java] om de UI-componenten te initialiseren die u in de speler wilt gebruiken.

1. Bewerk het [!DNL res/player/player_fragment.xml]-bestand om de gebruikersinterface aan te passen.
1. Bouw het project.

>[!NOTE]
>
>Als u UI-wijzigingen wilt aanbrengen in de zoekbalk, kunt u de klasse MarkableSeekBar bewerken. Met de klasse [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) worden de schuifregelaar, het blokje van de schuifregelaar, de houder van de markering, de actiemarkeringen, het bufferbereik en de achtergronden van het zoekbereik afgehandeld.