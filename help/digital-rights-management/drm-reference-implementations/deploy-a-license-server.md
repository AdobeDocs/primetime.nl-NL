---
description: 'null'
seo-description: 'null'
seo-title: De licentieserver implementeren
title: De licentieserver implementeren
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 29149594c4b41956a091ef27093304e74ff15f2f

---


# De licentieserver implementeren{#deploy-the-license-server}

1. Kopieer de oorlogsbestanden voor de verwijzingsimplementatie naar de `webapps` directory op uw Tomcat-server.

   Als u de licentieserver voor de voorbeeldimplementatie ongewijzigd wilt gebruiken, kopieert u gewoon het WAR-bestand ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) van de licentieserver naar de `webapps` directory op uw Tomcat-server.

   Als u de licentieserver voor de voorbeeldimplementatie aanpast, kopieert u de bestanden voor de serveroorlog die u van `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` naar de `webapps` directory hebt gemaakt.

   >[!NOTE]
   >
   >Als u eerder WAR-bestanden van de licentieserver hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-mappen in de [!DNL webapps] map op de Tomcat-server verwijderen:        >
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >Implementeer niet [!DNL edsws.war] tenzij u achterwaartse compatibiliteit met Flash Media Rights Management (FMRMS) v1.5-inhoud vereist. (Dit is een zeer zeldzame vereiste.)
   >
   >Als u liever wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u deze `server.xml` in de `conf` map en stelt u `unpackWARs` deze in op `false`.

1. Kopieer de volledige inhoud van de `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` map naar uw [!DNL tomcat] map.

   De [!DNL resources] map bevat:

   * [!DNL flashaccesstools.properties] - Het eigenschappenbestand van de licentieserver.
   * [!DNL log4j.xml] - Configuratie logboekregistratie licentieserver
   * [!DNL *.pol] - Voorbeelden van DRM-beleidsbestanden.
   Bovendien kunt u de Adobe-certificeringsbestanden naar deze locatie kopiëren.

1. Wijzig de instellingen van de licentieserver in [!DNL flashaccesstools.properties] de serverinstellingen.

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

1. Bewerk het `catalina.properties` bestand in de Tomcat- `conf` directory. Voeg de locatie van de [!DNL resources] map (of de alternatieve locatie waar u het eigenschappenbestand en andere bronbestanden hebt opgeslagen) toe aan de `shared.loader` eigenschap.

   Bijvoorbeeld, als u in [!DNL `flashaccess-refimpl.properties` Tomcat homepage [\resources\] hebt]gevestigd:

   ```
   shared.loader=..\resources
   ```

   Dit plaatst `flashaccess-refimpl.properties` het klassepad.
1. Zorg ervoor dat de andere bronbestanden ( [!DNL log4j.xml], beleidsbestanden, certificeringen) zich in de [!DNL resources] map bevinden of zich op een andere manier op het klassepad bevinden en dat de locatie van deze bestanden is opgegeven in [!DNL flashaccess-refimpl.properties].

   U zult waarschijnlijk op zuivert wijze aanvankelijk willen lopen `log4j` . Inpunt [!DNL log4j.xml], ingesteld `debug` op true:

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Start de server vanaf de Tomcat- [!DNL bin] directory.

   In Linux:

   ```
   catalina.sh start
   ```

   In Windows:

   ```
   catalina.bat start
   ```
