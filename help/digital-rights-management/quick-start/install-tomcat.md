---
seo-title: Tomcat installeren
title: Tomcat installeren
uuid: f7663eda-ad18-4a6e-bb9f-01c74721b047
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Tomcat installeren {#install-tomcat}

U moet Tomcat op beide servers installeren.
1. Installeer Tomcat vanuit de map [!DNL \Third Party\Tomcat\6.0.18\] op de installatie-dvd.

   >[!NOTE]
   >
   >Zorg ervoor dat Tomcat is geïnstalleerd op een locatie waar het pad geen spaties bevat. U kunt invoeren `C:\Program Files\Tomcat`, maar niet `C:\Tomcat\`.

1. Voer `TomcatInstallDir>\bin\catalina.bat run`in om Tomcat te starten.
1. Als u de installatie wilt controleren, gaat u naar de bestemmingspagina van Tomcat door deze in te voeren `https://<Hostname>:8080/`.
1. Maak een `crossdomain.xml` bestand en plaats het in de `<TomcatInstallDir>\webapps\ROOT\` map.

   U kunt ook een bestand uit de `https://drmtest2.adobe.com/crossdomain.xml` map kopiëren.
