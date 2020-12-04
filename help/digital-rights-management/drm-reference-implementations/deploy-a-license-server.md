---
description: 'null'
seo-description: 'null'
seo-title: De licentieserver implementeren
title: De licentieserver implementeren
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# De licentieserver implementeren{#deploy-the-license-server}

1. Kopieer de oorlogsbestanden voor de verwijzingsimplementatie naar de map `webapps` op uw Tomcat-server.

   Als u de licentieserver voor de referentie-implementatie ongewijzigd wilt gebruiken, kunt u het WAR-bestand van de licentieserver ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) gewoon kopiëren naar de map `webapps` op uw Tomcat-server.

   Als u de licentieserver voor de referentie-implementatie aanpast, kopieert u de bestanden voor de serveroorlog die u hebt gemaakt van `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` naar de map `webapps`.

   >[!NOTE]
   >
   >Als u eerder WAR-bestanden van de licentieserver hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-mappen verwijderen in de map [!DNL webapps] op de Tomcat-server:
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >Implementeer [!DNL edsws.war] alleen als u achterwaartse compatibiliteit met Flash Media Rights Management v1.5-inhoud (FMRMS) vereist. (Dit is een zeer zeldzame vereiste.)
   >
   >Als u liever wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u `server.xml` in de map `conf` en stelt u `unpackWARs` in op `false`.

1. Kopieer de volledige inhoud van de map `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` naar de map [!DNL tomcat].

   De map [!DNL resources] bevat:

   * [!DNL flashaccesstools.properties] - Het eigenschappenbestand van de licentieserver.
   * [!DNL log4j.xml] - Configuratie logboekregistratie licentieserver
   * [!DNL *.pol] - Voorbeelden van DRM-beleidsbestanden.

   Bovendien kunt u ervoor kiezen om de Adobe-certificeringsbestanden naar deze locatie te kopiëren.

1. Wijzig de instellingen van de licentieserver in [!DNL flashaccesstools.properties] om aan te geven hoe u de server instelt.

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

1. Bewerk het `catalina.properties`-bestand in de map Tomcat `conf`; Voeg de locatie van uw [!DNL resources]-map (of de alternatieve locatie waar u het eigenschappenbestand en andere bronbestanden hebt opgeslagen) toe aan de `shared.loader`-eigenschap.

   Als u bijvoorbeeld `flashaccess-refimpl.properties` hebt in [!DNL [Tomcat home]\resources\]:

   ```
   shared.loader=..\resources
   ```

   Hiermee plaatst u `flashaccess-refimpl.properties` op het klassepad.
1. Zorg ervoor dat uw andere bronbestanden ( [!DNL log4j.xml], beleidsbestanden, certificeringen) zich in de map [!DNL resources] bevinden of zich anders in het klassepad bevinden en dat de locatie ervan is opgegeven in [!DNL flashaccess-refimpl.properties].

   U zult waarschijnlijk `log4j` op zuivert wijze aanvankelijk willen in werking stellen. Stel `debug` in [!DNL log4j.xml] in op true:

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Start de server vanuit de Tomcat-directory [!DNL bin].

   In Linux:

   ```
   catalina.sh start
   ```

   In Windows:

   ```
   catalina.bat start
   ```
