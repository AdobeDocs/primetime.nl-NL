---
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
description: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Wachtwoorden voorbereiden voor de bestanden met servereigenschappen{#prepare-passwords-for-the-server-properties-files}

De referentie-implementatie biedt `ScrambleUtil.class`, een klasse die de veiligheid van het wachtwoord van uw referentie verzekert.

Met dit gereedschap kunt u het wachtwoord coderen voordat u het opneemt in het dialoogvenster [!DNL flashaccess-refimpl.properties] bestand.

Voor het uitvoeren van het gereedschap kunt u een Ant-script of Java gebruiken.

Het hulpprogramma genereert het gecodeerde wachtwoord, dat u naar de [!DNL flashaccess-refimpl.properties] bestand.

>[!NOTE]
>
>Wachtwoorden die met de `ScrambleUtil.class` die bij de referentie-implementatie is geleverd, werken niet met de Primetime DRM-server voor beveiligde streaming.
