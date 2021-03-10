---
title: Tomcat installeren
description: Tomcat installeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# Tomcat {#install-tomcat} installeren

U moet Tomcat op beide servers installeren.
1. Installeer Tomcat vanuit de map [!DNL \Third Party\Tomcat\6.0.18\] op de installatie-dvd.

   >[!NOTE]
   >
   >Zorg ervoor dat Tomcat is geïnstalleerd op een locatie waar het pad geen spaties bevat. U kunt `C:\Program Files\Tomcat`, maar niet `C:\Tomcat\` ingaan.

1. Typ `TomcatInstallDir>\bin\catalina.bat run` om Tomcat te starten.
1. Als u de installatie wilt controleren, gaat u naar de bestemmingspagina van Tomcat door `https://<Hostname>:8080/` in te voeren.
1. Maak een `crossdomain.xml`-bestand en plaats het bestand in de map `<TomcatInstallDir>\webapps\ROOT\`.

   U kunt ook een bestand uit de map `https://drmtest2.adobe.com/crossdomain.xml` kopiëren.
