---
description: U kunt eenvoudig een aangepaste gebruikersinterface maken op basis van het referentie-implementatieframework.
title: Een aangepaste gebruikersinterface maken
exl-id: 96008010-cd63-4fb1-a3fc-2fc94b624413
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '141'
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

1. Bewerk de [!DNL PlayerFragment.java] bestand om de UI-componenten te initialiseren die u in de speler wilt gebruiken.

1. Bewerk de [!DNL res/player/player_fragment.xml] bestand om de gebruikersinterface aan te passen.
1. Bouw het project.

>[!NOTE]
>
>Als u UI-wijzigingen wilt aanbrengen in de zoekbalk, kunt u de klasse MarkableSeekBar bewerken. De [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) De klasse handelt de schuifregelaar, het blokje van de schuifregelaar, de houder van de markering, de actiemarkeringen, het bufferbereik en de achtergronden van het zoekbereik af.
