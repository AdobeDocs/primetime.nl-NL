---
title: De database van de licentieserver instellen
description: De database van de licentieserver instellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
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
>Deze procedure geldt alleen voor Microsoft Windows. Voor andere besturingssystemen raadpleegt u de documentatie bij uw besturingssysteem of raadpleegt u de MySQL-documentatie.

Als u de licentieserver wilt uitvoeren, moet u MySQL installeren en configureren:

1. Ga op de dvd naar de [!DNL Third Party\MySQL\Installer\5.1] en start het installatieprogramma.
1. Verwerk de MySQL-installatie.
1. Selecteren **[!UICONTROL Configure MySQL Server Now]** om de configuratietovenaar te beginnen.
1. Tot het vijfde scherm, gebruik de standaardmontages of selecteer specifieke montages voor uw het testen.
1. Selecteer op het vijfde scherm de optie **[!UICONTROL Online Transaction Processing (OLTP)]** of **[!UICONTROL Manual Setting]** en voer het maximale aantal toegestane verbindingen in.
1. Schrijf het hoofdwachtwoord neer.
1. Voer de volgende stappen uit als u MySQL opnieuw wilt installeren als u de server later wilt starten:
   1. Verwijder de *systeemstation:* map.

      Deze map bevindt zich in [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. Verwijder de oude installatiemap voor MySQL.

      Bijvoorbeeld: *systeemstation:*, die zich bevindt in [!DNL \Program Files\MySQL\MySQL Server 5.1].
1. Als u MySQL JDBC Driver 5.1.7 wilt installeren, kopieert u de [!DNL mysql-connector-java-5.1.7-bin.jar] in het [!DNL Third Party\MySQL\Installer\5.1] naar de dvd [!DNL ...\Tomcat6.0\lib] op de Tomcat-server.

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 werkt met Tomcat 6.0. Oudere versies van Tomcat worden niet meer ondersteund.
