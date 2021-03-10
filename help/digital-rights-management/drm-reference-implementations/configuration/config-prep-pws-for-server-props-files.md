---
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
description: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '101'
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
