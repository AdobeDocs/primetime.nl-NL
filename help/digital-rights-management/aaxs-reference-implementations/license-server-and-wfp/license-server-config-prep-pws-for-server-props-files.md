---
title: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
description: Wachtwoorden voorbereiden voor de bestanden met servereigenschappen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Wachtwoorden voor de bestanden met servereigenschappen voorbereiden {#preparing-passwords-for-the-server-properties-files}

Om de veiligheid van het wachtwoord van uw referentie te verzekeren, wordt een hulpmiddel verstrekt om het wachtwoord te coderen alvorens het in [!DNL flashaccess-refimpl.properties] of [!DNL flashaccess-refimpl-packager.properties] dossier wordt ingegaan.

Het gereedschap uitvoeren met behulp van het volgende ANT-script:

* Ga naar *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* Zorg ervoor dat de eigenschap `sdkdir` in [!DNL build-refimpl.xml] verwijst naar de map met de Adobe Access SDK
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
