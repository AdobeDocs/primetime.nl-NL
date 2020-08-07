---
description: 'null'
seo-description: 'null'
seo-title: De database van de licentieserver instellen
title: De database van de licentieserver instellen
uuid: aa6185f2-8e9d-4b65-971a-b7534d910580
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# De database van de licentieserver instellen{#set-up-the-license-server-database}

Voor de licentieserver voor de implementatie van de referentie is een database vereist die het volgende ondersteunt:

* Gebruikersverificatie
* Gebruikersmodel demo bedrijfsregels
* Metagegevensomzetting
* Domeinondersteuning

De anonieme vergunningsverwerving vereist niet dat het gegevensbestand loopt.

>[!NOTE]
>
>Deze procedure is alleen van toepassing op Microsoft Windows. Voor andere besturingssystemen raadpleegt u de documentatie bij uw besturingssysteem of raadpleegt u de MySQL-documentatie.

Als u de licentieserver wilt uitvoeren, moet u MySQL installeren en configureren:

1. Ga op de dvd naar de [!DNL Third Party\MySQL\Installer\5.1] map en start het installatieprogramma.
1. Verwerk de MySQL-installatie.
1. Selecteer **[!UICONTROL Configure MySQL Server Now]** om de configuratietovenaar te beginnen.
1. Tot het vijfde scherm, gebruik de standaardmontages of selecteer specifieke montages voor uw het testen.
1. Selecteer op het vijfde scherm het maximum aantal toegestane verbindingen **[!UICONTROL Online Transaction Processing (OLTP)]** of **[!UICONTROL Manual Setting]** en voer het maximum aantal toegestane verbindingen in.
1. Schrijf het hoofdwachtwoord neer.
1. Voer de volgende stappen uit als u MySQL opnieuw wilt installeren als u de server later wilt starten:
   1. Verwijder het *systeemstation:* map.

      Deze map bevindt zich in [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Verwijder de oude installatiemap voor MySQL.

      Bijvoorbeeld, *systeemaandrijving:*, die in [!DNL \Program Files\MySQL\MySQL Server 5.1]. wordt gevestigd
1. Als u MySQL JDBC-stuurprogramma 5.1.7 wilt installeren, kopieert u het [!DNL mysql-connector-java-5.1.7-bin.jar] bestand in de [!DNL Third Party\MySQL\Installer\5.1] map op de dvd naar de [!DNL ...\Tomcat6.0\lib] map op de Tomcat-server.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 werkt met Tomcat 6.0. Oudere versies van Tomcat worden niet meer ondersteund.

