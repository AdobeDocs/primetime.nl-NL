---
description: U kunt eenvoudig een aangepaste gebruikersinterface maken op basis van het referentie-implementatieframework.
title: Een aangepaste gebruikersinterface maken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
