---
seo-title: Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren
title: Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren {#deploying-the-license-server-and-watched-folder-packager-overview}

Kopieer de WAR-bestanden van de licentieserver naar de [!DNL webapps] directory van Tomcat. Als u eerder het dossier van WAR hebt opgesteld, kunt u de onverpakte folders van de OORLOG ( [!DNL flashaccess], [!DNL edcws], en [!DNL flashaccess-packager] in de [!DNL webapps] folder van Tomcat) moeten manueel schrappen. Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml] bestand in de conf-map van Tomcat en stelt u het `unpackWARs` kenmerk in op `false`.

Het eigenschappenbestand ( [!DNL flashaccess-refimpl.properties]) moet zich op het klassepad bevinden om de eigenschappen te kunnen laden. Kopieer dit bestand naar een map en werk het bestand bij met de juiste waarden. Bewerk het [!DNL catalina.properties] bestand in de [!DNL conf] directory van Tomcat en voeg de map met het bestand toe [!DNL flashaccess-refimpl.properties] aan de `shared.loader` eigenschap. Het [!DNL log4j.xml] bestand voor het configureren van logbestanden moet zich ook op het klassepad bevinden (zie [!DNL resources\log4j.xml] voor een voorbeeld).

De server van de verwijzings implementatie gebruikt verscheidene certificaatdossiers, beleidsdossiers, en andere middelen. Deze bestanden bevinden zich allemaal in één bronnenmap. De bronnenmap is standaard [!DNL C:\flashaccess-server-resources]maar deze locatie kan worden gewijzigd in [!DNL flashaccess-refimpl.properties]. Kopieer alle vereiste bronnen naar deze locatie voordat u de server start.

Als u Tomcat en de licentieserver wilt starten, voert u deze uit `catalina.bat start` vanuit de [!DNL bin] directory van Tomcat.
