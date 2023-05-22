---
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
description: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
copied-description: true
exl-id: b613d43d-17ec-44e9-bd14-81f9bb9a7f62
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
>Wachtwoorden die zijn gecodeerd met de `ScrambleUtil.class` die bij de referentie-implementatie is geleverd, werken niet met de Primetime DRM-server voor beveiligde streaming.
