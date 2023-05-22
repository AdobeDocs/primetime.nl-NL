---
title: Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren
description: Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren
copied-description: true
exl-id: b44aec8b-f1d7-4dce-bc51-0ce2b74ae0c1
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Overzicht van de licentieserver en de gecontroleerde mapverpakker implementeren {#deploying-the-license-server-and-watched-folder-packager-overview}

De WAR-bestanden van de licentieserver kopiëren naar Tomcat [!DNL webapps] directory. Als u het WAR-bestand eerder hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-mappen handmatig verwijderen ( [!DNL flashaccess], [!DNL edcws], en [!DNL flashaccess-packager] in Tomcat [!DNL webapps] directory). Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u de opdracht [!DNL server.xml] bestand in de conf-map van Tomcat en stel de `unpackWARs` kenmerk naar `false`.

Het eigenschappenbestand ( [!DNL flashaccess-refimpl.properties]) moet zich op het klassepad bevinden, anders kan de server de eigenschappen niet laden. Kopieer dit bestand naar een map en werk het bestand bij met de juiste waarden. Bewerk de [!DNL catalina.properties] bestand in Tomcat [!DNL conf] en voeg de map toe die de map bevat [!DNL flashaccess-refimpl.properties] aan de `shared.loader` eigenschap. De [!DNL log4j.xml] bestand voor configureren van logbestand moet zich ook op het klassepad bevinden (zie [!DNL resources\log4j.xml] bijvoorbeeld).

De server van de verwijzings implementatie gebruikt verscheidene certificaatdossiers, beleidsdossiers, en andere middelen. Deze bestanden bevinden zich allemaal in één bronnenmap. Standaard is de bronnenmap [!DNL C:\flashaccess-server-resources], maar deze locatie kan worden gewijzigd in [!DNL flashaccess-refimpl.properties]. Kopieer alle vereiste bronnen naar deze locatie voordat u de server start.

Als u Tomcat en de licentieserver wilt starten, voert u `catalina.bat start` van Tomcat [!DNL bin] directory.
