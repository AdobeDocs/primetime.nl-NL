---
description: Met de server voor referentie-implementatie kunt u een volledig functionele licentieserver maken die alle functies van de Adobe Primetime DRM Java SDK gebruikt.
title: Licentieserver
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Licentieserver {#license-server}

Met de server voor referentie-implementatie kunt u een volledig functionele licentieserver maken die alle functies van de Adobe Primetime DRM Java SDK gebruikt.

In deze implementatie worden gebruikers geverifieerd op basis van gebruikersinvoer in een database. De server omvat demonstratie bedrijfslogica voor het uitgeven van vergunningen en verleent verenigbaarheidssteun voor de Server 1.0 en 1.5 van het Rights Management van de Media van de Flash.

## Vereisten voor licentieservers {#license-server-requirements}

Vereisten voor licentieserver:

* Tomcat 6.0 of hoger installeren
* Installeer een database, bijvoorbeeld MySQL (beschikbaar op de dvd, in [!DNL Third Party\MySQL])
* Zorg ervoor dat Java 1.6 of hoger is geïnstalleerd
* Om de steekproef in werking te stellen bouwt manuscripten, zorg ervoor dat u Ant 1.8 of later hebt

Nadat u Tomcat en MySQL hebt geïnstalleerd, neemt u contact op met de Adobe voor uw set vereiste DRM-referenties.

## De licentieserver samenstellen {#build-the-license-server}

>[!NOTE]
>
>Het samenstellen van de licentieserver is alleen nodig als u van plan bent de broncode te wijzigen. Voor evaluatiedoeleinden kunt u de WAR-bestanden gewoon gebruiken zoals ze worden verzonden.

De licentieserver voor de voorbeeldimplementatie bevat alle broncode van de licentieserver ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`), samen met een Ant-constructiescript ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`) waarmee u de licentieserver kunt aanpassen aan uw bedrijfsbehoeften.

1. Wijzig Ant bouwt manuscript om de plaatsen van uw Primetime DRM SDK, Tomcat, MySQL, en Log4J te specificeren.

   Open de [!DNL build-refimpl.xml] bestand in een teksteditor en stel de volgende eigenschapswaarden in:

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Het Ant-constructiescript uitvoeren met het `all` eigenschap, in de map waarin het Ant-constructiescript zich bevindt.

   ```
   ant -f build-refimpl.xml all
   ```

   Met het Ant-constructiescript wordt een [!DNL refimpl-build/wars] map die de WAR-bestanden van de server bevat.
