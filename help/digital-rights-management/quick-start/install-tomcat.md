---
title: Tomcat installeren
description: Tomcat installeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Tomcat installeren {#install-tomcat}

U moet Tomcat op beide servers installeren.
1. Tomcat installeren vanuit de [!DNL \Third Party\Tomcat\6.0.18\] op de installatie-dvd.

   >[!NOTE]
   >
   >Zorg ervoor dat Tomcat is geïnstalleerd op een locatie waar het pad geen spaties bevat. U kunt `C:\Program Files\Tomcat`, maar niet `C:\Tomcat\`.

1. Als u Tomcat wilt starten, voert u `TomcatInstallDir>\bin\catalina.bat run`.
1. Als u de installatie wilt controleren, gaat u naar de bestemmingspagina van Tomcat door `https://<Hostname>:8080/`.
1. Een `crossdomain.xml` en plaats het bestand in het `<TomcatInstallDir>\webapps\ROOT\` directory.

   U kunt ook een bestand kopiëren uit het dialoogvenster `https://drmtest2.adobe.com/crossdomain.xml` directory.
