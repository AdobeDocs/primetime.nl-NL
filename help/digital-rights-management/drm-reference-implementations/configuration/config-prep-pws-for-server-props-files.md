---
description: 'null'
seo-description: 'null'
seo-title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Wachtwoorden voorbereiden voor de bestanden met servereigenschappen{#prepare-passwords-for-the-server-properties-files}

De verwijzingsimplementatie verstrekt `ScrambleUtil.class`, een klasse die de veiligheid van het wachtwoord van uw referentie verzekert.

Gebruik dit hulpmiddel om het wachtwoord te coderen alvorens u het in het [!DNL flashaccess-refimpl.properties] dossier opneemt.

Voor het uitvoeren van het gereedschap kunt u een Ant-script of Java gebruiken.

Het hulpprogramma genereert het gecodeerde wachtwoord dat u naar het [!DNL flashaccess-refimpl.properties] bestand moet kopiëren.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Wachtwoorden die zijn gecodeerd met de `ScrambleUtil.class` referentie-implementatie werken niet met de Primetime DRM-server voor beveiligde streaming.
