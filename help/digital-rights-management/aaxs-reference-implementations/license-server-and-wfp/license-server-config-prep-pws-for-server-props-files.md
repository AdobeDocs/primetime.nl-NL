---
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
description: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
copied-description: true
exl-id: 70f75640-7075-450a-8191-dc348bd269b8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Wachtwoorden voorbereiden voor de bestanden met servereigenschappen {#preparing-passwords-for-the-server-properties-files}

Om de veiligheid van het wachtwoord van uw referentie te verzekeren, wordt een hulpmiddel verstrekt om het wachtwoord te coderen alvorens het in het [!DNL flashaccess-refimpl.properties] of [!DNL flashaccess-refimpl-packager.properties] bestand.

Het gereedschap uitvoeren met behulp van het volgende ANT-script:

* Ga naar *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* Zorg ervoor dat de `sdkdir` eigenschap in [!DNL build-refimpl.xml] verwijst naar de map met de SDK van Adobe Access
* Voer het volgende bevel in werking gebruikend ANT:

   ```
       ant -f build-refimpl.xml
   ```

* Typ desgevraagd het wachtwoord van uw referentie

Het gereedschap uitvoeren met Java:

* Ga naar *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* Van de bevelherinnering, ga het bevel in:

* In Windows:

   ```
   java -classpath path_to_adobe-flashaccess-sdk.jar;.  
   com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

* In Linux:

   ```
       java -classpath path_to_adobe-flashaccess-sdk.jar;.  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

Het nut output het gecodeerde wachtwoord, dat u aan het .properties- dossier moet kopiëren.

>[!NOTE]
>
>Wachtwoorden die zijn gecodeerd met het hulpprogramma voor wachtwoordcodering dat is meegeleverd bij de referentie-implementatie, werken niet met de Adobe Access Server voor beveiligde streaming.
