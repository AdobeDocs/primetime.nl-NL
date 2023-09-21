---
title: De licentieserver implementeren
description: De licentieserver implementeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# De licentieserver implementeren{#deploy-the-license-server}

1. Kopieer uw oorlogsbestanden voor de implementatie van de referentie naar de `webapps` op uw Tomcat-server.

   Als u de licentieserver voor de voorbeeldimplementatie ongewijzigd wilt gebruiken, kunt u gewoon het WAR-bestand van de licentieserver kopiëren ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) aan de `webapps` op uw Tomcat-server.

   Als u de licentieserver voor de voorbeeldimplementatie aanpast, kopieert u de serveroorlogsbestanden die u hebt gemaakt `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` aan de `webapps` directory.

   >[!NOTE]
   >
   >Als u eerder WAR-bestanden van de licentieserver hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-mappen verwijderen in het dialoogvenster [!DNL webapps] directory op de Tomcat-server:
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]

   >[!NOTE]
   >
   >Niet implementeren [!DNL edsws.war] tenzij u achterwaartse compatibiliteit met Flash Media Rights Management (FMRMS) v1.5 inhoud vereist. (Dit is een zeer zeldzame vereiste.)
   >
   >Als u liever wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u `server.xml` in de `conf` map en set `unpackWARs` tot `false`.

1. Kopieer de volledige inhoud van het dialoogvenster `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` in uw [!DNL tomcat] directory.

   De [!DNL resources] map bevat:

   * [!DNL flashaccesstools.properties] - Het eigenschappenbestand van de licentieserver.
   * [!DNL log4j.xml] - Configuratie logboekregistratie licentieserver
   * [!DNL *.pol] - Voorbeelden van DRM-beleidsbestanden.

   Daarnaast kunt u ook de certificaatbestanden voor de Adobe naar deze locatie kopiëren.

1. Instellingen van licentieserver wijzigen in [!DNL flashaccesstools.properties] om de serverinstelling te weerspiegelen.

   Stel ten minste waarden in voor de volgende eigenschappen:

   * `config.resourcesDirectory`
   * `HandlerConfiguration.ServerTransportCredential`
   * `HandlerConfiguration.ServerTransportCredential.password`
   * `LicenseHandler.ServerCredential`
   * `LicenseHandler.ServerCredential.password`
   * `MetaDataConverter.SignatureParameters.ServerCredential`
   * `MetaDataConverter.SignatureParameters.ServerCredential.password`
   * `V2KeyParameters.LicenseServerUrl`
   * `V2KeyParameters.KeyOptions.AsymmetricKeyOptions.Certificate`
   * V2KeyParameters.LicenseServerTransportCertificate

1. Bewerk de `catalina.properties` bestand in uw Tomcat `conf` directory; voeg de locatie van uw [!DNL resources] map (of de alternatieve locatie waar u het eigenschappenbestand en andere bronbestanden hebt opgeslagen) naar de `shared.loader` eigenschap.

   Als u bijvoorbeeld `flashaccess-refimpl.properties` bevindt zich in [!DNL [Tomcat home]\resources\]:

   ```
   shared.loader=..\resources
   ```

   Deze plaatsen `flashaccess-refimpl.properties` op het klassepad.
1. Zorg ervoor dat uw andere bronbestanden ( [!DNL log4j.xml], beleidsbestanden, certificeringen) bevinden zich in de [!DNL resources] directory of bevinden zich op een andere manier op het klassepad en de locatie die is opgegeven in [!DNL flashaccess-refimpl.properties].

   U wilt waarschijnlijk eerst uitvoeren `log4j` in de foutopsporingsmodus. In [!DNL log4j.xml], set `debug` naar waar:

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Van de Tomcat [!DNL bin] Start de server.

   In Linux:

   ```
   catalina.sh start
   ```

   In Windows:

   ```
   catalina.bat start
   ```
