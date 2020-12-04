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


# Database van de licentieserver instellen{#set-up-the-license-server-database}

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

1. Ga op de dvd naar de map [!DNL Third Party\MySQL\Installer\5.1] en start het installatieprogramma.
1. Verwerk de MySQL-installatie.
1. Selecteer **[!UICONTROL Configure MySQL Server Now]** om de configuratietovenaar te beginnen.
1. Tot het vijfde scherm, gebruik de standaardmontages of selecteer specifieke montages voor uw het testen.
1. Selecteer **[!UICONTROL Online Transaction Processing (OLTP)]** of **[!UICONTROL Manual Setting]** op het vijfde scherm en voer het maximale aantal toegestane verbindingen in.
1. Schrijf het hoofdwachtwoord neer.
1. Voer de volgende stappen uit als u MySQL opnieuw wilt installeren als u de server later wilt starten:
   1. Verwijder het *systeemstation:*-map.

      Deze map bevindt zich in [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Verwijder de oude installatiemap voor MySQL.

      Bijvoorbeeld *systeemstation:*, dat zich in [!DNL \Program Files\MySQL\MySQL Server 5.1] bevindt.
1. Als u MySQL JDBC-stuurprogramma 5.1.7 wilt installeren, kopieert u het [!DNL mysql-connector-java-5.1.7-bin.jar]-bestand in de map [!DNL Third Party\MySQL\Installer\5.1] op de dvd naar de map [!DNL ...\Tomcat6.0\lib] op de Tomcat-server.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 werkt met Tomcat 6.0. Oudere versies van Tomcat worden niet meer ondersteund.

