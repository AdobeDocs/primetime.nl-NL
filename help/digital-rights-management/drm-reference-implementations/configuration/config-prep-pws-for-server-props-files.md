---
description: 'null'
seo-description: 'null'
seo-title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Wachtwoorden voorbereiden voor de bestanden met servereigenschappen{#prepare-passwords-for-the-server-properties-files}

De verwijzingsimplementatie verstrekt `ScrambleUtil.class`, een klasse die de veiligheid van het wachtwoord van uw referentie verzekert.

Gebruik dit hulpmiddel om het wachtwoord te coderen alvorens u het in het [!DNL flashaccess-refimpl.properties] dossier opneemt.

Voor het uitvoeren van het gereedschap kunt u een Ant-script of Java gebruiken.

Het nut produceert het gecodeerde wachtwoord, dat u aan het [!DNL flashaccess-refimpl.properties] dossier moet kopiëren.

>[!NOTE]
>
>Wachtwoorden die zijn gecodeerd met de `ScrambleUtil.class` die zijn meegeleverd bij de referentie-implementatie, werken niet met de Primetime DRM-server voor beveiligde streaming.
