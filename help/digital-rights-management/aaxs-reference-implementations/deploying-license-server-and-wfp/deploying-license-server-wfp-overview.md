---
seo-title: Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren
title: Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Overzicht van de licentieserver en de gecontroleerde omslagverpakker {#deploying-the-license-server-and-watched-folder-packager-overview} implementeren

Kopieer de WAR-bestanden van de licentieserver naar de map [!DNL webapps] van Tomcat. Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-mappen ( [!DNL flashaccess], [!DNL edcws] en [!DNL flashaccess-packager] in de map [!DNL webapps] van Tomcat) handmatig verwijderen. Om te voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml]-bestand in de conf-map van Tomcat en stelt u het `unpackWARs`-kenmerk in op `false`.

Het eigenschappenbestand ( [!DNL flashaccess-refimpl.properties]) moet zich op het klassepad bevinden om de eigenschappen te kunnen laden. Kopieer dit bestand naar een map en werk het bestand bij met de juiste waarden. Bewerk het [!DNL catalina.properties]-bestand in de map [!DNL conf] van Tomcat en voeg de map met [!DNL flashaccess-refimpl.properties] toe aan de eigenschap `shared.loader`. Het [!DNL log4j.xml] dossier voor het vormen van registreren moet ook op classpath (zie [!DNL resources\log4j.xml] voor een voorbeeld) zijn.

De server van de verwijzings implementatie gebruikt verscheidene certificaatdossiers, beleidsdossiers, en andere middelen. Deze bestanden bevinden zich allemaal in één bronnenmap. Standaard is de bronnenmap [!DNL C:\flashaccess-server-resources], maar deze locatie kan worden gewijzigd in [!DNL flashaccess-refimpl.properties]. Kopieer alle vereiste bronnen naar deze locatie voordat u de server start.

Als u Tomcat en de licentieserver wilt starten, voert u `catalina.bat start` uit vanuit de directory [!DNL bin] van Tomcat.
